import java.util.ArrayList;
import java.util.Scanner;

class Kitap {
    String baslik;
    String yazar;

    Kitap(String baslik, String yazar) {
        this.baslik = baslik;
        this.yazar = yazar;
    }

    public String toString() {
        return "Başlık: " + baslik + " | Yazar: " + yazar;
    }
}

public class Kutuphane {
    static ArrayList<Kitap> kitaplar = new ArrayList<>();
    static Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        int secim;

        do {
            System.out.println("\n=== KÜTÜPHANE SİSTEMİ ===");
            System.out.println("1. Kitap Ekle");
            System.out.println("2. Kitapları Listele");
            System.out.println("0. Çıkış");
            System.out.print("Seçiminiz: ");
            secim = scanner.nextInt();
            scanner.nextLine(); // Enter'ı tüket

            switch (secim) {
                case 1:
                    kitapEkle();
                    break;
                case 2:
                    kitaplariListele();
                    break;
                case 0:
                    System.out.println("Çıkılıyor...");
                    break;
                default:
                    System.out.println("Geçersiz seçim. Tekrar deneyin.");
            }
        } while (secim != 0);
    }

    public static void kitapEkle() {
        System.out.print("Kitap başlığı: ");
        String baslik = scanner.nextLine();

        System.out.print("Yazar adı: ");
        String yazar = scanner.nextLine();

        Kitap yeniKitap = new Kitap(baslik, yazar);
        kitaplar.add(yeniKitap);
        System.out.println("Kitap eklendi!");
    }

    public static void kitaplariListele() {
        if (kitaplar.isEmpty()) {
            System.out.println("Henüz hiç kitap eklenmedi.");
        } else {
            System.out.println("\n--- KİTAP LİSTESİ ---");
            for (Kitap kitap : kitaplar) {
                System.out.println(kitap);
            }
        }
    }
}
