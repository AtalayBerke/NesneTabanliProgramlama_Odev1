# NesneTabanliProgramlama_Odev1

//Admin Girişi 


using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Data.SqlClient;

namespace OkulOdev1
{
   
    public partial class AnaForm : Form
    {
        public AnaForm()
        {
            InitializeComponent();
        }
        SqlConnection bgl = new SqlConnection("Data Source=DESKTOP-LC55U5G\\SQLEXPRESS;Initial Catalog=OkulOdev1;Integrated Security=True");
        

        private void Form2_Load(object sender, EventArgs e)
        {
            
            
        }

        
        private void button1_Click(object sender, EventArgs e)
        {
            bgl.Open();
            SqlCommand komut = new SqlCommand("Select * from Table_USER where Username=@P1 and Password=@P2",bgl);
            komut.Parameters.AddWithValue("@P1", txtusername.Text);
            komut.Parameters.AddWithValue("@P2", txtpassword.Text);
            SqlDataReader dr=komut.ExecuteReader();
            if (dr.Read()) //EĞER OKUYABİLİYORSA 
            {
                MessageBox.Show("Başarılı");
            }
            else
            {
                MessageBox.Show("Başarısız");
            }
            bgl.Close();
        }

        private void linkLabel1_LinkClicked(object sender, LinkLabelLinkClickedEventArgs e)
        {
            this.Hide();
            Frm_Sifreyenile fr = new Frm_Sifreyenile();
            fr.Show();
        }

        private void linkLabel2_LinkClicked(object sender, LinkLabelLinkClickedEventArgs e)
        {
            Frm_Sifre_2 fr = new Frm_Sifre_2();
            fr.Show();
            this.Hide();
        }
    }
}
