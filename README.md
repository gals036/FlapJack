# FlapJack
algoritma pemrograman dari FlapJack

package flapjack36;
import java.io.BufferedReader; // untuk mendapat input dari keyboard
import java.io.IOException; // 
import java.io.InputStreamReader; //  
 // fungsi dari java.io sama dengan scanner, io bisa menginput melalui keyboars maupun file
public class Flapjack36 {

    public static void main(String[] args) throws NumberFormatException, IOException { // mainclass
        BufferedReader in = new BufferedReader(new InputStreamReader(System.in)); // memanggil bufferedreader
        System.out.println("Masukkan data : ");
		String s = " "; //variabel s bertipe string
		while((s = in.readLine()) != null) { // proses akan terus berjalan selama inputan tidak kosong
			String batas = " ";// variabel batas tipe string
			String[] str = s.split(" "); // deklarasi string dengan array (str), split= pembagi antara bagian yang akan dibalik dan yang tidak dibalik
			int[] a = new int[str.length]; // array a tipe integer dengan jumlah panjang sesuai panjang array str
			for(int i = 0 ; i < str.length; i++) { // mencari nilai maximal pada array 
				a[i] = Integer.parseInt(str[i]);// merubah tipe data menjadi int setalah tadi diproses secara string
			}
                        // setelah nilai max ditemukan maka lanjut ke proses selanjutnya                        
			for(int i = a.length - 1; i > 0;  i--) { // selanjutnya proses flip data, flip dilakukan dari indeks terbesar
				int letak = getMaxPos(a, i);// masuk di prosedur getMax Position (array, posisi indeks dari nilai maksimal di array tersebut)
				if(a[0] == a[letak]) { 
					flip(a, a.length - i);//perintah untuk memanggil flip
					batas += (a.length - i) + " "; 
				}// keadaan true posisi pembatas tidak perlu diubah kembali
				else { // jika posisi pembatas (pembalik) yang harus di ubah tidak tepat maka diubah posisi pembatasnya
					int move = a.length - letak;// mindah posisi pembatas
					batas += move + " ";
					flip(a, move);
					batas += (a.length - i) + " ";
					flip(a, a.length - i);
				}
				if(check(a))
					break;
                        
			}
                        System.out.print("Proses pengurutan data : ");
			System.out.println(batas);
                        System.out.println("ini mas hasilnya :");
                        for (int i = 0; i < a.length; i++) {
                            System.out.print(a[i] + " ");
                    }
		}
 
	} // prosedur yang akan di akses 
 
        
                
	private static boolean check(int[] a) { // untuk ngecek apabila urutan benar maka tdk perlu di proses kembali
		for(int i = 0; i < a.length - 1; i++) {  
			if(a[i] > a[i + 1]) // jika kondisi sesuai, maka hasil false dan proses dilanjutkan
				return false;
		}
		return true;
	}// proses chek data dari atas satu persatu
 
	private static void flip(int[] a, int start) { // untuk melakukan porses flip
		
		int s = a.length - start;
		for(int i = s, j = 0; j < (s + 1)/2; i--, j++) {
			int tmp = a[i];// temp=penyimpanan sementara nilai a[i]
			a[i] = a[j];// nilai a[i] diganti a [j] 
			a[j] = tmp;// nilai a [j] diganti dengan tmp yang isinya adalah nilai a[i] 
		}
	}
        
	private static int getMaxPos(int[] a, int range) { // mencari nilai terbesar 
		int max = 0, letak = 0; 
		for(int i = 0; i <= range; i++) 
			if(a[i] > max) { // jika a [i] lebih besar dari max
				max = a[i];// maka nilai max diganti dengan niali a[i] tersebut
				letak = i;
			}
		return letak;// terus memproses selama masih dalam indeks
	}
}
    


