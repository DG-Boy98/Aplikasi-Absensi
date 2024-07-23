import java.util.*;

// Kelas Mahasiswa untuk merepresentasikan data mahasiswa
class Mahasiswa {
    private String nama;
    private boolean hadir;

    public Mahasiswa(String nama) {
        this.nama = nama;https://github.com/github-copilot/signup
        this.hadir = false; // Default: tidak hadir
    }

    public String getNama() {
        return nama;
    }

    public boolean isHadir() {
        return hadir;
    }

    public void setHadir(boolean hadir) {
        this.hadir = hadir;
    }
}

// Kelas AplikasiAbsensi sebagai main program
public class AplikasiAbsensi {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ArrayList<Mahasiswa> daftarMahasiswa = new ArrayList<>();

        // Menambahkan beberapa mahasiswa ke dalam daftar
        daftarMahasiswa.add(new Mahasiswa("Deden"));
        daftarMahasiswa.add(new Mahasiswa("Gilang"));
        daftarMahasiswa.add(new Mahasiswa("Supriatna"));

        boolean lanjut = true;

        while (lanjut) {
            // Menampilkan menu
            System.out.println("\nMenu:");
            System.out.println("1. Tampilkan daftar mahasiswa");
            System.out.println("2. Tandai kehadiran mahasiswa");
            System.out.println("3. Keluar");
            System.out.print("Pilih menu (1/2/3): ");
            
            // Membaca pilihan dari pengguna
            int pilihan = scanner.nextInt();

            switch (pilihan) {
                case 1:
                    // Menampilkan daftar nama mahasiswa
                    System.out.println("\nDaftar Mahasiswa:");
                    for (Mahasiswa mhs : daftarMahasiswa) {
                        System.out.println(mhs.getNama() + " - Hadir: " + (mhs.isHadir() ? "Ya" : "Tidak"));
                    }
                    break;
                case 2:
                    // Tandai kehadiran mahasiswa
                    System.out.print("\nMasukkan nama mahasiswa yang hadir: ");
                    scanner.nextLine(); // Menangani newline character
                    String namaMhs = scanner.nextLine();

                    boolean ditemukan = false;
                    for (Mahasiswa mhs : daftarMahasiswa) {
                        if (mhs.getNama().equalsIgnoreCase(namaMhs)) {
                            mhs.setHadir(true);
                            System.out.println("Kehadiran untuk " + mhs.getNama() + " berhasil ditandai.");
                            ditemukan = true;
                            break;
                        }
                    }

                    if (!ditemukan) {
                        System.out.println("Mahasiswa dengan nama " + namaMhs + " tidak ditemukan.");
                    }
                    break;
                case 3:
                    // Keluar dari program
                    System.out.println("Terima kasih!");
                    lanjut = false;
                    break;
                default:
                    System.out.println("Pilihan tidak valid. Silakan pilih menu yang tersedia.");
            }
        }

        scanner.close();
    }
}
