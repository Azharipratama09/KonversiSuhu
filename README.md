# KonversiSuhu
 Tugas 2-Muhammad Azhari Nur Pratama-221001326
 
# 1. Deskripsi Program
• Pengguna memasukkan nilai suhu dan memilih jenis konversi
• Hasil konversi ditampilkan setelah tombol ditekan.

# 2. Komponen GUI: 
JFrame, JPanel, JLabel, JTextField, JComboBox, JButton,

# 3. Logika Program:
Rumus konversi, validasi input
   
# 4. Events

• ActionListener untuk tombol Konversi
~~~
    private void jButton1ActionPerformed(java.awt.event.ActionEvent evt) {                                         
     try {
            double inputSuhu = Double.parseDouble(jTextField1.getText());
            String hasilKonversi = (String) jComboBox1.getSelectedItem();
            double hasil = 0.0;

        // Periksa arah konversi berdasarkan pilihan JRadioButton
        if (jRadioButton1.isSelected()) {
            // Konversi dari Celsius ke skala yang dipilih
            switch (hasilKonversi) {
                case "Celsius ke Fahrenheit":
                    hasil = celsiusToFahrenheit(inputSuhu);
                    break;
                case "Celsius ke Kelvin":
                    hasil = celsiusToKelvin(inputSuhu);
                    break;
                case "Celsius ke Reamur":
                    hasil = celsiusToReamur(inputSuhu);
                    break;
                default:
                    JOptionPane.showMessageDialog(this, "Pilihan konversi tidak valid!");
                    break;
                    
            }
        } else if (jRadioButton2.isSelected()) {
            // Konversi dari Fahrenheit ke skala yang dipilih
            switch (hasilKonversi) {
                case "Fahrenheit ke Celsius":
                    hasil = fahrenheitToCelsius(inputSuhu);
                    break;
                case "Fahrenheit ke Kelvin":
                    hasil = fahrenheitToKelvin(inputSuhu);
                    break;
                case "Fahrenheit ke Reamur":
                    hasil = fahrenheitToReamur(inputSuhu);
                    break;
                default:
                    JOptionPane.showMessageDialog(this, "Pilihan konversi tidak valid!");
                    break;    
            }
      } else if (jRadioButton5.isSelected()) {
            switch (hasilKonversi) {
                case "Kelvin ke Celsius":
                    hasil = kelvinToCelsius(inputSuhu);
                    break;
                case "Kelvin ke Fahrenheit":
                    hasil = kelvinToFahrenheit(inputSuhu);
                    break;
                case "Kelvin ke Reamur":
                    hasil = kelvinToReamur(inputSuhu);
                    break;
                default:
                    JOptionPane.showMessageDialog(this, "Pilihan konversi tidak valid!");
                    break;
            }
        } else if (jRadioButton6.isSelected()) {
            switch (hasilKonversi) {
                case "Reamur ke Celsius":
                    hasil = reamurToCelsius(inputSuhu);
                    break;
                case "Reamur ke Fahrenheit":
                    hasil = reamurToFahrenheit(inputSuhu);
                    break;
                case "Reamur ke Kelvin":
                    hasil = reamurToKelvin(inputSuhu);
                    break;
                default:
                    JOptionPane.showMessageDialog(this, "Pilihan konversi tidak valid!");
                    break;
                }
            }

         jLabel4.setText("" + hasil);
        } catch (NumberFormatException e) {
            JOptionPane.showMessageDialog(this, "Masukkan angka yang valid!");
        }
                                               
    }     
   ~~~   
• Tombol Konversi diklik akan menampilkan hasil konversi dari
~~~
// Dari Celsius ke skala lain
private double celsiusToFahrenheit(double celsius) {
    return (celsius * 9/5) + 32;
}

private double celsiusToReamur(double celsius) {
    return celsius * 4/5;
}

private double celsiusToKelvin(double celsius) {
    return celsius + 273.15;
}
// Dari Fahrenheit ke skala lain
private double fahrenheitToCelsius(double fahrenheit) {
    return (fahrenheit - 32) * 5/9;
}

private double fahrenheitToReamur(double fahrenheit) {
    return (fahrenheit - 32) * 4/9;
}

private double fahrenheitToKelvin(double fahrenheit) {
    return (fahrenheit - 32) * 5/9 + 273.15;
} 
~~~

5. Variasi:
• Tambahkan skala suhu lain seperti Reamur dan Kelvin
~~~
// Dari Kelvin
private double kelvinToCelsius(double kelvin) {
    return kelvin - 273.15;
}

private double kelvinToFahrenheit(double kelvin) {
    return (kelvin - 273.15) * 9/5 + 32;
}

private double kelvinToReamur(double kelvin) {
    return (kelvin - 273.15) * 4/5;
}
    
// Dari Reamur
private double reamurToCelsius(double reamur) {
    return reamur * 5/4;
}

private double reamurToFahrenheit(double reamur) {
    return reamur * 9/4 + 32;
}

private double reamurToKelvin(double reamur) {
    return reamur * 5/4 + 273.15;
}

~~~
• Tambahkan ItemListener pada JRadioButton untuk memilih arah konversi
~~~
    private void jRadioButton1ItemStateChanged(java.awt.event.ItemEvent evt) {                                               
    if (evt.getStateChange() == ItemEvent.SELECTED) {
            jComboBox1.removeAllItems();
            jComboBox1.addItem("Celsius ke Fahrenheit");
            jComboBox1.addItem("Celsius ke Kelvin");
            jComboBox1.addItem("Celsius ke Reamur");
        }   

    }                                              

    private void jRadioButton2ItemStateChanged(java.awt.event.ItemEvent evt) {                                               
        if (evt.getStateChange() == ItemEvent.SELECTED) {
            jComboBox1.removeAllItems();
            jComboBox1.addItem("Fahrenheit ke Celsius");
            jComboBox1.addItem("Fahrenheit ke Kelvin");
            jComboBox1.addItem("Fahrenheit ke Reamur");
        }
    }     

    private void jRadioButton5ItemStateChanged(java.awt.event.ItemEvent evt) {                                               
      if (evt.getStateChange() == ItemEvent.SELECTED) {
            jComboBox1.removeAllItems();
            jComboBox1.addItem("Kelvin ke Celsius");
            jComboBox1.addItem("Kelvin ke Fahrenheit");
            jComboBox1.addItem("Kelvin ke Reamur");
        }
    }                                              

    private void jRadioButton6ItemStateChanged(java.awt.event.ItemEvent evt) {                                               
        if (evt.getStateChange() == ItemEvent.SELECTED) {
            jComboBox1.removeAllItems();
            jComboBox1.addItem("Reamur ke Celsius");
            jComboBox1.addItem("Reamur ke Fahrenheit");
            jComboBox1.addItem("Reamur ke Kelvin");
        }

    }   
    } 

 ~~~
• Implementasikan konversi otomatis saat nilai input berubah
~~~
private void setupDocumentListener(){
        InputSuhutxt.getDocument().addDocumentListener(new DocumentListener() {
            @Override
            public void insertUpdate(DocumentEvent e) {
                btnKonversiActionPerformed();
            }

            @Override
            public void removeUpdate(DocumentEvent e) {
                btnKonversiActionPerformed();
            }

            @Override
            public void changedUpdate(DocumentEvent e) {
                btnKonversiActionPerformed();
            }        

            private void btnKonversiActionPerformed() {
                 //To change body of generated methods, choose Tools | Templates.
            }
        });  
}
~~~

## Hasil Setelah Di Run
![Cuplikan layar 2024-11-05 213723](https://github.com/user-attachments/assets/2e6e9e2b-37cc-4d32-9c92-4e674a83f167)


## Indikator Penilaian:

| No  | Komponen         |  Persentase  |
| :-: | --------------   |   :-----:    |
|  1  | Komponen GUI     |    10    |
|  2  | Logika Program   |    20    |
|  3  | Kesesuaian UI    |    15    |
|  4  | Constructor      |    15    |
|  5  | Memenuhi Variasi |    40    |
|     | TOTAL        | 100 |

## Pembuat

Nama  : Muhammad Azhari Nur Pratama
NPM   : 2210010326
