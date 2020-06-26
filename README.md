# kbh14789.github.io
import java.util.Arrays;
import java.util.Random;

public class Main {

    public static int[] init() {
        Random r = new Random();
        int[] arr = new int[4];
        for (int i = 0; i < 4; i++) {
            arr[i] = r.nextInt(21);
        }
        return arr;
    }

    public static int MSE(int a, int b, int[] x, int[] y)
    {
        int MSE = 0;
        for(int i = 0 ;i < y.length; i++)
        {
            MSE += Math.pow(y[i]-a*x[i]+b,2);
        }
        return MSE;
    }

    public static int[] selection(int[] a, int[] x, int[] y) {
        int sum = 0;
        int[] f = new int[a.length];
        Arrays.fill(f, Integer.MAX_VALUE);
        for (int i = 0; i < a.length; i++) {
            for (int j = 20; j <= 50; j++) {
                f[i] = Math.min(f[i], MSE(a[i],j,x,y));
            }
            sum += f[i];
        }

        for (int i = 0; i < a.length; i++) {
            f[i] = sum - f[i];
        }

        sum = 0;
        for (int i = 0; i < a.length; i++) {
            sum += f[i];
        }

        double[] ratio = new double[a.length];
        for (int i = 0; i < a.length; i++) {
            if (i == 0) ratio[i] = (double) f[i] / (double) sum;
            else ratio[i] = ratio[i - 1] + (double) f[i] / (double) sum;
        }


        int[] sx = new int[a.length];
        Random r = new Random();
        for (int i = 0; i < a.length; i++) {
            double p = r.nextDouble();
            if (p < ratio[0]) sx[i] = a[0];
            else if (p < ratio[1]) sx[i] = a[1];
            else if (p < ratio[2]) sx[i] = a[2];
            else sx[i] = a[3];
        }

        System.out.print("selection: ");
        for (int i = 0; i <4; i++) {
            System.out.printf("%d ", sx[i]);
        }
        System.out.println();

        return sx;
    }

    public static String int2String(String x) {
        return String.format("%8s", x).replace(' ', '0');
    }

    public static String[] crossOver(int[] x) {
        String[] arr = new String[x.length];
        for (int i = 0; i < x.length; i += 2) {
            String bit1 = int2String(Integer.toBinaryString(x[i]));
            String bit2 = int2String(Integer.toBinaryString(x[i + 1]));

            arr[i] = bit1.substring(0, 4) + bit2.substring(4, 8);
            arr[i + 1] = bit2.substring(0, 4) + bit1.substring(4, 8);
        }

        System.out.print("crossover: ");
        for (int i = 0; i < 4; i++) {
            System.out.printf("%s ", arr[i]);
        }
        System.out.println();

        return arr;
    }

    public static int invert(String x) {
        Random r = new Random();
        int a = Integer.parseInt(x, 2);
        for (int i = 0; i < x.length(); i++) {
            double p = (double) 1 / (double) 50;
            if (r.nextDouble() < p) {
                a = 1 << i ^ a;
            }
        }
        return a;
    }

    public static int[] mutation(String[] x) {
        int[] arr = new int[x.length];
        for (int i = 0; i < x.length; i++) {
            arr[i] = invert(x[i]);
        }
        return arr;
    }


    public static void main(String[] args) {


        int[] a = init();
        int[] x = new int[30];
        for(int i = 0; i < 30; i++) {
            x[i] = i;
        }

        int[] y = new int[30];
        for(int i = 0; i < 30; i++) {
            Random r = new Random();
            y[i] = 3*x[i] + 25 + (int)(20*r.nextGaussian());
            System.out.printf("해: %d %d\n", x[i], y[i]);
        }
        int result_a = 0;
        int result_b = 0;

        for(int i=0; i<1000; i++) {
            System.out.print("후보해 : ");
            for (int j = 0; j < 4; j++) {
                System.out.printf("%d ", a[j]);
            }
            System.out.println();

            int[] sx = selection(a, x, y);
            String[] cx = crossOver(sx);
            int[] mx = mutation(cx);

            int[] f = new int[mx.length];
            int min = Integer.MAX_VALUE;
            for(int j = 0; j < mx.length; j++) {
                for(int k = 20; k <= 50; k++) {
                    f[j] = MSE(a[j], k, x, y);
                    if (min > f[j]) {
                        min = f[j];
                        result_a = a[j];
                        result_b = k;
                    }
                }
            }

            a = mx;

            System.out.print("mutation: ");
            for (int j = 0; j < 4; j++) {
                System.out.printf("%d ", a[j]);
            }
            System.out.println();

            System.out.println("y=" + result_a + "x+" + result_b);
            System.out.println();
        }
    }
}




![컴알 그래프 해](https://user-images.githubusercontent.com/62762126/85860455-c9498600-b7f9-11ea-9ba1-528ed9281f23.JPG)


![컴알 그래프 최종 해](https://user-images.githubusercontent.com/62762126/85860461-cbabe000-b7f9-11ea-9a4e-bdef3e28f5ad.JPG)


![컴알 그래프](https://user-images.githubusercontent.com/62762126/85859368-044aba00-b7f8-11ea-914f-5f98b3457652.JPG)
