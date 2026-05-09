import java.util.Scanner;
class Menu {
    String nama;
    int harga;
    String kategori;

    Menu(String nama, int harga, String kategori) {
        this.nama = nama;
        this.harga = harga;
        this.kategori = kategori;
    }
}





public class Main {

    public static void tampilMenu(Menu[] Menu) {

        System.out.println("===== MENU MAKANAN =====");
        System.out.println("1. " + Menu[0].nama + " = Rp " + Menu[0].harga);
        System.out.println("2. " + Menu[1].nama + " = Rp " + Menu[1].harga);
        System.out.println("3. " + Menu[2].nama + " = Rp " + Menu[2].harga);
        System.out.println("4. " + Menu[3].nama + " = Rp " + Menu[3].harga);

        System.out.println("\n===== MENU MINUMAN =====");
        System.out.println("5. " + Menu[4].nama + " = Rp " + Menu[4].harga);
        System.out.println("6. " + Menu[5].nama + " = Rp " + Menu[5].harga);
        System.out.println("7. " + Menu[6].nama + " = Rp " + Menu[6].harga);
        System.out.println("8. " + Menu[7].nama + " = Rp " + Menu[7].harga);
    }

    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);
         System.out.println("Program berjalan");

    


        Menu[] menu = {
            new Menu("Nasi Goreng", 25000, "Makanan"),
            new Menu("Bebek Goreng", 35000, "Makanan"),
            new Menu("Ayam Geprek", 20000, "Makanan"),
            new Menu("Ikan Bakar", 45000, "Makanan"),

            new Menu("Es Teh", 5000, "Minuman"),
            new Menu("Jus Alpukat", 15000, "Minuman"),
            new Menu("Es Jeruk", 8000, "Minuman"),
            new Menu("Air Mineral", 5000, "Minuman")
        };

        tampilMenu(menu);

        // Pesanan maksimal 4
        int[] pilihan = new int[4];
        int[] jumlah = new int[4];

        System.out.println("\n===== INPUT PESANAN =====");

        System.out.print("Pesanan 1 (nomor menu): ");
        pilihan[0] = input.nextInt();
        System.out.print("Jumlah: ");
        jumlah[0] = input.nextInt();

        System.out.print("Pesanan 2 (nomor menu): ");
        pilihan[1] = input.nextInt();
        System.out.print("Jumlah: ");
        jumlah[1] = input.nextInt();

        System.out.print("Pesanan 3 (nomor menu): ");
        pilihan[2] = input.nextInt();
        System.out.print("Jumlah: ");
        jumlah[2] = input.nextInt();

        System.out.print("Pesanan 4 (nomor menu): ");
        pilihan[3] = input.nextInt();
        System.out.print("Jumlah: ");
        jumlah[3] = input.nextInt();

        // Hitung subtotal
        int subtotal1 = menu[pilihan[0]-1].harga * jumlah[0];
        int subtotal2 = menu[pilihan[1]-1].harga * jumlah[1];
        int subtotal3 = menu[pilihan[2]-1].harga * jumlah[2];
        int subtotal4 = menu[pilihan[3]-1].harga * jumlah[3];

        int total = subtotal1 + subtotal2 + subtotal3 + subtotal4;

        // Promo beli 1 gratis 1 minuman
        int diskonMinuman = 0;

        if(total > 50000) {

    if(menu[pilihan[0]-1].kategori.equals("Minuman")
            && jumlah[0] >= 2) {

        diskonMinuman = menu[pilihan[0]-1].harga;
            }
        }

        // Diskon 10%
        double diskon = 0;

        if(total > 100000) {
            diskon = total * 0.10;
        }

        // Pajak
        double pajak = total * 0.10;

        // Biaya pelayanan
        int pelayanan = 5000;

        // Total akhir
        double totalBayar =
                total + pajak + pelayanan
                - diskon - diskonMinuman;

        // Cetak struk
        System.out.println("\n===== STRUK PEMBAYARAN =====");

        System.out.println(menu[pilihan[0]-1].nama +
                " x " + jumlah[0] +
                " = Rp " + subtotal1);

        System.out.println(menu[pilihan[1]-1].nama +
                " x " + jumlah[1] +
                " = Rp " + subtotal2);

        System.out.println(menu[pilihan[2]-1].nama +
                " x " + jumlah[2] +
                " = Rp " + subtotal3);

        System.out.println(menu[pilihan[3]-1].nama +
                " x " + jumlah[3] +
                " = Rp " + subtotal4);

        System.out.println("--------------------------------");

        System.out.println("Total Harga      : Rp " + total);
        System.out.println("Pajak 10%        : Rp " + pajak);
        System.out.println("Biaya Pelayanan  : Rp " + pelayanan);
        System.out.println("Diskon           : Rp " + diskon);
        System.out.println("Promo Minuman    : Rp " + diskonMinuman);

        System.out.println("--------------------------------");

        System.out.println("Total Bayar      : Rp " + totalBayar);
        input.close();
    }
}
