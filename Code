using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace WindowsFormsApp4
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        static int n = 3; // Number of processes
        static int m = 4; // Number of resources
        int[,] need = new int[n, m];
        int[,] max = new int[n, m];
        string[,] allocate = new string[n, m];
        string[,] maximum = new string[n, m];
        int[,] alloc = new int[n, m];
        int[] avail = new int[4];
        int[] safeSequence = new int[n];
        int[] nofresources = new int[m];
        string choosen_p;
        string choosen_R;
        int nofR;
        List<int> f = new List<int>();
        public Dictionary<string, int> mapping = new Dictionary<string, int>();

      
        private void button1_Click(object sender, EventArgs e)
        {







            allocate[0, 0] = textBox1.Text;
            allocate[0, 1] = textBox2.Text;
            allocate[0, 2] = textBox3.Text;
            allocate[0, 3] = textBox33.Text;
            allocate[1, 0] = textBox4.Text;
            allocate[1, 1] = textBox5.Text;
            allocate[1, 2] = textBox6.Text;
            allocate[1, 3] = textBox34.Text;
            allocate[2, 0] = textBox7.Text;
            allocate[2, 1] = textBox8.Text;
            allocate[2, 2] = textBox9.Text;
            allocate[2, 3] = textBox35.Text;




            //allocation matrix calcaulations
            for (int i = 0; i < 3; i++)
            {
                for (int j = 0; j < 4; j++)
                {
                    alloc[i, j] = int.Parse(allocate[i, j]);
                }
            }
            maximum[0, 0] = textBox10.Text;
            maximum[0, 1] = textBox11.Text;
            maximum[0, 2] = textBox12.Text;
            maximum[0, 3] = textBox28.Text;
            maximum[1, 0] = textBox13.Text;
            maximum[1, 1] = textBox14.Text;
            maximum[1, 2] = textBox15.Text;
            maximum[1, 3] = textBox29.Text;
            maximum[2, 0] = textBox16.Text;
            maximum[2, 1] = textBox17.Text;
            maximum[2, 2] = textBox18.Text;
            maximum[2, 3] = textBox30.Text;



            //max matrix calcaulations
            for (int i = 0; i < 3; i++)
            {
                for (int j = 0; j < 4; j++)
                {
                    max[i, j] = int.Parse(maximum[i, j]);

                }
            }



            //nofresourses input // 
            nofresources[0] = int.Parse(textBox20.Text);
            nofresources[1] = int.Parse(textBox21.Text);
            nofresources[2] = int.Parse(textBox22.Text);
            nofresources[3] = int.Parse(textBox31.Text);

            //availaible matrix calcaulation

            avail[0] = int.Parse(textBox24.Text);
            avail[1] = int.Parse(textBox25.Text);
            avail[2] = int.Parse(textBox26.Text);
            avail[3] = int.Parse(textBox32.Text);


            mapping.Add("A", 0);
            mapping.Add("B", 1);
            mapping.Add("C", 2);
            mapping.Add("D", 3);

            mapping.Add("P1", 0);
            mapping.Add("P2", 1);
            mapping.Add("P3", 2);

            List<int> f = new List<int>();

            nofR = int.Parse(textBox27.Text);


            if (textBox19.Text == "A") 
                choosen_R = "A";
            else if(textBox19.Text =="B")
                choosen_R = "B";
            else if(textBox19.Text =="C")
                choosen_R = "C";
            else if(textBox19.Text =="D")
                choosen_R = "D";


            if (radioButton1.Checked)
                    choosen_p = "P1";
                else if (radioButton2.Checked)
                    choosen_p = "P2";
                else if (radioButton3.Checked)
                    choosen_p = "P3";

            read_request();


            for (int i = 0; i < 3; i++)
            {
                for (int j = 0; j < 4; j++)
                {
                    need[i, j] = max[i, j] - alloc[i, j];

                }
            }

            if (BankerAlgorithm())
            {
                MessageBox.Show("System is Safe");
            }
            else
            {
                MessageBox.Show("System is UnSafe");
            }









        }

        public void read_request()
        {
            int h = mapping[choosen_R];

            int k = mapping[choosen_p];

            alloc[h,k] = alloc[h,k] + nofR;
        }

        public bool BankerAlgorithm()
        {
            bool safe = true;
            bool flag = true;
            int counter = 0;

            for (int i = 0; i < 3; i++)
            {
                if (!f.Contains(i))
                {
                    for (int j = 0; j < 4; j++)
                    {
                        if (need[i, j] > avail[j])
                        {
                            flag = false;
                            counter++;
                        }
                    }

                    if (flag)
                    {
                        for (int t = 0; t < 4; t++)
                        {
                            avail[t] = alloc[i, t] + avail[t];
                        }

                        f.Add(i);
                        BankerAlgorithm();
                    }
                }
            }

            if (counter == 3)
                return false;
            return true;
        }
        private void radioButton1_CheckedChanged(object sender, EventArgs e)
        {
            radioButton1.Checked = true;
        }

        private void radioButton2_CheckedChanged(object sender, EventArgs e)
        {
            radioButton2.Checked = true;
        }

        private void radioButton3_CheckedChanged(object sender, EventArgs e)
        {
            radioButton3.Checked = true;
        }

        
    }

} 

        


    

    

