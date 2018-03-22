import java.security.PrivateKey;
import javax.swing.*;
import javax.xml.soap.Text;
import java.awt.*;
import com.sun.deploy.config.JCPConfig;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.JLabel;
import javax.swing.JFrame;



public class exa extends JFrame {


        private JTextField num,num2;
        private JButton btnAceptar;
        private  JLabel impresion;

        public exa (String titulo) {
            this.setTitle(titulo);
            this.setResizable(false);
            this.setLayout(null);
            Container panelPrinc = this.getContentPane();
            panelPrinc.setBackground(Color.blue);
            this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

            JLabel lblsegundos = new JLabel("Introducir el numero: ");
            lblsegundos.setBounds(10, 10, 140, 30);
            panelPrinc.add(lblsegundos);

            JLabel lblDinero = new JLabel("Introducir el numero: ");
            lblDinero.setBounds(10, 10, 140, 30);
            panelPrinc.add(lblDinero);

            num = new JTextField();
            num.setBounds(180, 10, 100, 30);
            panelPrinc.add(num);

            num2 = new JTextField(6);
            num2.setBounds(180, 50, 400, 30);
            panelPrinc.add(num2);

            //Creación de objetos que generan eventos
            btnAceptar = new JButton("Convertir");
            btnAceptar.setBounds(60, 110, 140, 30);
            panelPrinc.add(btnAceptar);

            //crear oyente
            AccionBoton oyenteBtnConver = new AccionBoton();
            //crear vinculo
            btnAceptar.addActionListener(oyenteBtnConver);

        }

        class AccionBoton implements ActionListener {
            @Override
            //Método controlador del evento actionPerformed

            public void actionPerformed(ActionEvent e) {


                    int valor = Integer.parseInt(num.getText());

                    if (valor<1000000) {

                        long dia, hor, min, seg;
                        dia = valor / 86400;
                        hor = (valor - (86400 * dia)) / 3600;
                        min = valor % 3600 / 60;
                        seg = valor % 60;

                        num2.setText("dias: " + dia + " Horas:  " + hor + " minutos: " + min + " Segundos: " + seg);

                    }
                    else
                    {
                        num2.setText("El valor es superior a 1 millon");
                    }



            }

    }


        public static void main(String[] args)
    {
        exa f = new exa ("Examen");
        f.setSize(600,300);
        f.setLocation(90,0);
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        f.setVisible(true);
    }
}
