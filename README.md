# Aplikasi-Sederhana-Reservasi-Hotel
• Dibuat dengan menggunakan bahasa pemrograman Java. 
• Dibantu dengan Notepad++ dan Java Development Kit (JDK).

	import java.text.DateFormat;
	import java.text.SimpleDateFormat;
	import java.util.Calendar;
	import java.util.Date;
	import javax.swing.*;  
	import java.awt.*;  
	import java.awt.event.*;
	public class ReservasiHotel extends Frame implements ActionListener{
 
		JFrame frame1;
		JTextField nama;
		JTextField hp;
		JTextField checkin;
		JTextField hari;
		JLabel ljudul;
		JLabel lwelcome;
		JLabel lnama, lnama2;
		JLabel lhp, lhp2;
		JLabel lcheckin, lcheckin2;
		JLabel lhari, lhari2;
		JLabel ltipe, ltipe2;
		JLabel lharga;
		JLabel lcheckout;
		JComboBox tipe;
		JButton oke, reset;
		ReservasiHotel (){

    		//Menampilkan Judul Program
		JFrame frame1 = new JFrame ("Reservasi Hotel");
		ljudul = new JLabel (" ");
		ljudul.setBounds (280, 390, 150, 20);
		
		//Menampilkan Ucapan "Selamat Datang"
		lwelcome = new JLabel ("WELCOME TO GRAND EDGE HOTEL");
		lwelcome.setBounds (100, 30, 500, 20);
		lwelcome.setFont (new Font ("Arial Black", Font.PLAIN, 25));
		lwelcome.setForeground (new Color (0, 102, 204));
		
		//Menampilkan Tempat untuk Mengisi Data 
		lnama = new JLabel ("Nama :");
		lnama.setBounds (50, 70, 150, 20);
		nama = new JTextField ();
		nama.setBounds (250, 70, 150, 20);
		lnama2 = new JLabel ();
		lnama2.setBounds (220, 420, 150, 20);
		lhp = new JLabel ("No. Handphone :");
		lhp.setBounds (50, 120, 150, 20);
		hp = new JTextField ();
		hp.setBounds (250, 120, 150, 20);
		lhp2 = new JLabel ();
		lhp2.setBounds (220, 440, 300, 20);
		
		//Memilih Tipe Kamar dengan JComboBox
		ltipe = new JLabel ("Tipe Kamar :");
		ltipe.setBounds (50, 170, 300, 20);
   		String types[] = {"President (Rp 1.000.000/hari)", "Suite (Rp 500.000/hari)", "Superior (Rp 375.000/hari)", "Deluxe (Rp 300.000/hari)", "Standard (Rp 275.000/hari)"};        
		final JComboBox tipe = new JComboBox (types);    
		tipe.setBounds (250, 170, 200, 20);
		ltipe2 = new JLabel ();
		ltipe2.setBounds (220, 460, 300, 20);
		
		//Menampilkan Tempat untuk Mengisi Data
		lcheckin = new JLabel ("Check In (dd/mm/yy) :");
		lcheckin.setBounds(50, 220, 150, 20);
		checkin = new JTextField ();
		checkin.setBounds (250, 220, 150, 20);
		lcheckin2 = new JLabel ();
		lcheckin2.setBounds (220, 480, 150, 20);
		lhari = new JLabel ("Lama Menginap (Hari) :");
		lhari.setBounds (50, 270, 150, 20);
		hari = new JTextField ();
		hari.setBounds (250, 270, 150, 20);
		lhari2 = new JLabel ();
		lhari2.setBounds (220, 500, 300, 20);

    		//Menggunakan JButton untuk Menampilkan Hasil Input Data
		JButton oke = new JButton ("Oke");  
		oke.setBounds (190, 330, 95, 30);
		oke.addActionListener (this);
		JButton reset = new JButton ("Reset");  
		reset.setBounds (350, 330, 95, 30);
		reset.addActionListener (null);
		
		//Menampilkan Tanggal Check Out dan Total Harga
		lcheckout = new JLabel ();		
		lcheckout.setBounds (220, 520, 200, 20);
		lharga = new JLabel ();
		lharga.setBounds (220, 540, 300, 20);

    		frame1.add (nama);
		frame1.add (hp);
		frame1.add (checkin);
		frame1.add (hari);
		frame1.add (ljudul);
		frame1.add (lwelcome);
		frame1.add (lnama); frame1.add (lnama2);
		frame1.add (lhp); frame1.add (lhp2);
		frame1.add (lcheckin); frame1.add (lcheckin2);
		frame1.add (lhari); frame1.add (lhari2);
		frame1.add (ltipe); frame1.add (ltipe2);
		frame1.add (lharga);
		frame1.add (lcheckout);
		frame1.add (tipe);
		frame1.add (oke); frame1.add (reset);
		frame1.setSize (700,630);
		frame1.setLayout (null);  
		frame1.setVisible (true);

    		//Menampilkan Hasil Akhir Input Data dengan Tombol "Oke"
		oke.addActionListener (new ActionListener (){
			public String kelas;
			public int harga;
			public int lama;
			public void actionPerformed (ActionEvent e){
				
				//Menghitung Total Harga dengan If Else sesuai dengan Tipe Kamar yang Dipilih
				String jenis = "Tipe Kamar : "   
				+ tipe.getItemAt (tipe.getSelectedIndex ());

        			//Convert String to Integer
				int lama = Integer.parseInt (hari.getText ());
				kelas = (String) tipe.getSelectedItem();
				if (kelas == "Standard (Rp 275.000/hari)"){
					harga = lama*275000;
				}  
				else if (kelas == "Deluxe (Rp 300.000/hari)"){
					harga = lama*300000;
				}
				else if (kelas == "Superior (Rp 375.000/hari)"){
					harga = lama*375000;
				}
				else if (kelas == "Suite (Rp 500.000/hari)"){
					harga = lama*500000;
				}
				else if (kelas == "President (Rp 1.000.000/hari)"){
					harga = lama*1000000;
				}
				
				//Menampilkan Tipe Kamar yang Dipilih dan Total Harga
				ltipe2.setText (jenis);
				lharga.setText (String.valueOf ("Total Harga : Rp."+harga));
			}  
		});

    		//Menghapus Input Data dengan Tombol "Reset",sehingga Data Dapat Diisi secara Berulang
		reset.addActionListener (new ActionListener (){
			public void actionPerformed (ActionEvent e){
				nama.setText ("");
				hp.setText ("");
				checkin.setText ("");
				hari.setText ("");
			}
		});
	}
	
	//Menampilkan Hasil Input Data berdasarkan TextField yang Diisi
	public void actionPerformed (ActionEvent e){  
		try{ 
			ljudul.setText ("RESERVASI HOTEL");
			String host = nama.getText ();   			
			lnama2.setText ("Nama : "+host);
			String host2 = hp.getText ();
			lhp2.setText ("No. Handphone : "+host2);			
			String host3 = hari.getText ();   
			lhari2.setText ("Lama Menginap : "+host3 +" hari");

     			//Menampilkan Tanggal CheckOut berdasarkan Tanggal Check In dan Lama Menginap (Hari)
			DateFormat df = new SimpleDateFormat("dd/MM/yyyy"); 
			Date date = df.parse (checkin.getText ()); 
			lcheckin2.setText ("Check In : "+df.format (date));
			
			//Convert String to Integer
			int host4 = Integer.parseInt (hari.getText ());
			Calendar calTambah = Calendar.getInstance ();
			calTambah.setTime (date);
			calTambah.add (Calendar.DAY_OF_MONTH, host4);
			
			//Menampilkan Tanggal Check Out
			lcheckout.setText ("Check Out : "+df.format (calTambah.getTime ()));
		}
		catch (Exception ex) {System.out.println (ex);} 
	}
	public static void main (String[] args){  
        new ReservasiHotel ();  
    } 
}

