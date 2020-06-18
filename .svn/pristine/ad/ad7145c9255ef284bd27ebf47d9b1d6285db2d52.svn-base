using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using MIS;
using System.Globalization;
using System.Data.SqlClient;

namespace NewInfomationHouse
{
    public partial class Infobranch : MetroFramework.Forms.MetroForm
    {
        int state=0;
        string classid;
        SqlCommand command;
        DataSet ds = new DataSet();
        SqlConnection connection = misdb.MISMsSqlConnect("172.18.0.53","in-house", "foxuser", "foxpro");
        StringBuilder sb = new StringBuilder();

        public Infobranch()
        {
            InitializeComponent();
        }

        private void Infobranch_Load(object sender, EventArgs e)
        {
           
            panelBranch.Enabled = false;

            disp_grid();
            dataGridView1.ClearSelection();
            getcombo();
            btncancel.Enabled = false;
            btn_save.Enabled = false;
        }

        public void disp_grid() {
          
            SqlConnection connection = misdb.MISMsSqlConnect("172.18.0.53", "in-house", "foxuser", "foxpro");
            connection.Open();
            SqlCommand cmd = connection.CreateCommand();
            cmd.CommandType = CommandType.Text;
            // cmd.CommandText = "SELECT a.branchid as 'รหัสสาขา',a.branchname as 'ชื่อสาขา',a.shotname as 'ชื่อย่อ',a.zone as 'โซน',c.classname as 'ประเภท'  FROM branchdetail a INNER JOIN category c ON a.classid=c.classid";
             cmd.CommandText = "SELECT a.*,c.classname,c.classid as typeid FROM branchdetail a INNER JOIN category c ON a.classid=c.classid";

            DataTable dt = new DataTable();
            SqlDataAdapter da = new SqlDataAdapter(cmd);
            da.Fill(dt);
            dataGridView1.DataSource = null;
            //show
            dataGridView1.AutoGenerateColumns = false;
            dataGridView1.ColumnCount = 25;
            dataGridView1.Columns[0].Name = "branchid";
            dataGridView1.Columns[0].DataPropertyName = "branchid";
            dataGridView1.Columns[1].Name = "branchname";
            dataGridView1.Columns[1].DataPropertyName = "branchname";
            dataGridView1.Columns[2].Name = "shotname";
            dataGridView1.Columns[2].DataPropertyName = "shotname";
            this.dataGridView1.Columns[2].Visible = false;
            dataGridView1.Columns[3].Name = "zone";
            dataGridView1.Columns[3].DataPropertyName = "zone";
           
            //hide
               
            dataGridView1.Columns[4].Name = "typeid";
            dataGridView1.Columns[4].DataPropertyName = "typeid";
            this.dataGridView1.Columns[4].Visible = false;
            dataGridView1.Columns[5].Name = "room_id";
            dataGridView1.Columns[5].DataPropertyName = "room_id";
            this.dataGridView1.Columns[5].Visible = false;
            dataGridView1.Columns[6].Name = "areaid";
            dataGridView1.Columns[6].DataPropertyName = "areaid";
            this.dataGridView1.Columns[6].Visible = false;
            dataGridView1.Columns[7].Name = "total_area";
            dataGridView1.Columns[7].DataPropertyName = "total_area";
            this.dataGridView1.Columns[7].Visible = false;
            dataGridView1.Columns[8].Name = "use_area";
            dataGridView1.Columns[8].DataPropertyName = "use_area";
            this.dataGridView1.Columns[8].Visible = false;
            dataGridView1.Columns[9].Name = "stock_area";
            dataGridView1.Columns[9].DataPropertyName = "stock_area";
            this.dataGridView1.Columns[9].Visible = false;
            dataGridView1.Columns[10].Name = "room_number";
            dataGridView1.Columns[10].DataPropertyName = "room_number";
            this.dataGridView1.Columns[10].Visible = false;
            dataGridView1.Columns[11].Name = "opendate";
            dataGridView1.Columns[11].DataPropertyName = "opendate";
            this.dataGridView1.Columns[11].Visible = false;
            dataGridView1.Columns[12].Name = "address1";
            dataGridView1.Columns[12].DataPropertyName = "address1";
            this.dataGridView1.Columns[12].Visible = false;
            dataGridView1.Columns[13].Name = "address2";
            dataGridView1.Columns[13].DataPropertyName = "address2";
            this.dataGridView1.Columns[13].Visible = false;
            dataGridView1.Columns[14].Name = "tumbol";
            dataGridView1.Columns[14].DataPropertyName = "tumbol";
            this.dataGridView1.Columns[14].Visible = false;
            dataGridView1.Columns[15].Name = "aumper";
            dataGridView1.Columns[15].DataPropertyName = "aumper";
            this.dataGridView1.Columns[15].Visible = false;
            dataGridView1.Columns[16].Name = "province";
            dataGridView1.Columns[16].DataPropertyName = "province";
            this.dataGridView1.Columns[16].Visible = false;
            dataGridView1.Columns[17].Name = "zipcode";
            dataGridView1.Columns[17].DataPropertyName = "zipcode";
            this.dataGridView1.Columns[17].Visible = false;
            dataGridView1.Columns[18].Name = "tel01";
            dataGridView1.Columns[18].DataPropertyName = "tel01";
            this.dataGridView1.Columns[18].Visible = false;
            dataGridView1.Columns[19].Name = "tel02";
            dataGridView1.Columns[19].DataPropertyName = "tel02";
            this.dataGridView1.Columns[19].Visible = false;
            dataGridView1.Columns[20].Name = "tel03";
            dataGridView1.Columns[20].DataPropertyName = "tel03";
            this.dataGridView1.Columns[20].Visible = false;
            dataGridView1.Columns[21].Name = "tel03";
            dataGridView1.Columns[21].DataPropertyName = "tel03";
            this.dataGridView1.Columns[21].Visible = false;
            dataGridView1.Columns[22].Name = "managername";
            dataGridView1.Columns[22].DataPropertyName = "managername";
            this.dataGridView1.Columns[22].Visible = false;
            dataGridView1.Columns[23].Name = "employees_number";
            dataGridView1.Columns[23].DataPropertyName = "employees_number";
            this.dataGridView1.Columns[23].Visible = false;
            dataGridView1.Columns[24].Name = "classname";
            dataGridView1.Columns[24].DataPropertyName = "classname";
            this.dataGridView1.Columns[24].Visible = false;

            dataGridView1.DataSource = dt;

            cmd.ExecuteNonQuery();
            connection.Close();

        }

        private void getcombo()
        {
           
            sb.Remove(0, sb.Length);
            sb.Append("SELECT RTRIM(classid) as classid,RTRIM(classname) as classname FROM category");
            string cSql = sb.ToString();
            /*MySqlConnection Mycnn = misdb.MISMySqlConnect("jib");*/
            try
            {
                SqlDataAdapter Myda = new SqlDataAdapter(cSql, connection);
                connection.Open();
                SqlCommandBuilder MyComb = new SqlCommandBuilder(Myda);
                if (ds.Tables.Contains("class"))
                {
                    ds.Tables["class"].Clear();
                }
                Myda.Fill(ds, "class");

                cboClassid.DataSource = ds.Tables["class"];
                cboClassid.ValueMember = "classid";
                cboClassid.DisplayMember = "classname";

                connection.Close();
                connection.Dispose();
            }
            catch (SqlException ex)
            {
                MessageBox.Show(ex.ToString());
            }
        }

        private void btnnew_Click(object sender, EventArgs e)
        {
            state = 1;
            panelBranch.Enabled = true;
            btn_save.Enabled = true;
            btncancel.Enabled = true;
            clearTextbox();
        }

        private void btncancel_Click(object sender, EventArgs e)
        {
            panelBranch.Enabled = false;
            dataGridView1.Enabled = true;
           
        }

        private void btn_save_Click(object sender, EventArgs e)
        {
            var culture = new CultureInfo("en-GB");
            decimal totalarea; decimal usearea; decimal stockarea; int roomnumber; int empnum;

            string branchid = txtBranchid.Text;
            string branchname = txtBranchname.Text;
            string shotname = txtShotname.Text;
            string zone = txtZone.Text;
            int classidint = Convert.ToInt32(classid);
            string room_id = txtRoom_id.Text;
            string areaid = txtAreaid.Text;
            string opendate = dtOpendate.Value.ToString("yyyy-MM-dd", culture);
            string address1 = txtAddress1.Text;
            string address2 = txtAddress2.Text;
            string tumbol = txtTumbol.Text;
            string aumper = txtAumper.Text;
            string province = txtProvince.Text;
            string zipcode = txtZipcode.Text;
            string tel01 = txtTel01.Text;
            string tel02 = txtTel02.Text;
            string tel03 = txtTel03.Text;
            string managername = txtManagername.Text;
           
            if (String.IsNullOrEmpty(txtTotalarea.Text))
            {
                totalarea = 0;
            }
            else
            {
                totalarea = Convert.ToDecimal(txtTotalarea.Text);
            }
            if (String.IsNullOrEmpty(txtUse_area.Text))
            {
                usearea = 0;
            }
            else
            {
                usearea = Convert.ToDecimal(txtUse_area.Text);
            }
            if (String.IsNullOrEmpty(txtStock_area.Text))
            {
                stockarea = 0;
            }
            else
            {
                stockarea = Convert.ToDecimal(txtStock_area.Text);
            }

            if (String.IsNullOrEmpty(txtRoom_number.Text))
            {
                roomnumber = 0;
            }
            else
            {
                roomnumber = Convert.ToInt32(txtRoom_number.Text);
            }

            if (String.IsNullOrEmpty(txtEmployees_number.Text))
            {
                empnum = 0;
            }
            else
            {
                empnum = Convert.ToInt32(txtEmployees_number.Text);
            }
            
            //INSERT
            if (state==1) {
                if (String.IsNullOrEmpty(txtBranchid.Text))
                {
                    MessageBox.Show("ป้อนรหัสสาขาแล้วหรือยัง?");
                }
                else
                {  
                    SqlConnection connection = misdb.MISMsSqlConnect("172.18.0.53", "in-house", "foxuser", "foxpro");
                    string str = "INSERT INTO dbo.branchdetail values('" + branchid + "','" + branchname + "','" + shotname + "','" + zone + "','" + classidint + "','" + room_id + "','" + areaid + "','" + totalarea + "','" + usearea + "','" + stockarea + "','" + roomnumber + "','" + opendate + "','" + address1 + "','" + address2 + "','" + tumbol + "','" + aumper + "','" + province + "','" + zipcode + "','" + tel01 + "','" + tel02 + "','" + tel03 + "',GETDATE(),'" + managername + "','" + empnum + "')";      
                    try
                    {
                        connection.Open();
                        command = new SqlCommand(str, connection);
                        SqlDataReader dr1 = command.ExecuteReader();
                        connection.Close();
                        disp_grid();
                        MessageBox.Show("ระบบบันทึกข้อมูลเรียบร้อยแล้ว (save is successful++)");
                        btncancel.Enabled = false;
                        btn_save.Enabled = false;
                        panelBranch.Enabled = false;
                        state = 0;
                    }
                    catch (SqlException ex) {
                        MessageBox.Show(ex.ToString());
                    }
                }
            //UPDATE
            } else if(state==2){
                if (String.IsNullOrEmpty(txtBranchid.Text))
                {
                    MessageBox.Show("ป้อนรหัสสาขาแล้วหรือยัง?");
                }
                else
                {
                    SqlConnection connection = misdb.MISMsSqlConnect("172.18.0.53", "in-house", "foxuser", "foxpro");
                    string str = "UPDATE  dbo.branchdetail SET branchid='"+ branchid+ "',branchname ='" + branchname + "',shotname='" + shotname + "',zone='" + zone + "',classid='" + classidint + "',room_id='" + room_id + "',areaid='" + areaid + "',total_area='" + totalarea + "',use_area='" + usearea + "',stock_area='" + stockarea + "',room_number='" + roomnumber + "',opendate='" + opendate + "',address1='" + address1 + "',address2='" + address2 + "',tumbol='" + tumbol + "',aumper='" + aumper + "',province='" + province + "',zipcode='" + zipcode + "',tel01='" + tel01 + "',tel02='" + tel02 + "',tel03='" + tel03 + "',upd=GETDATE(),managername='" + managername + "',employees_number='"+empnum+"' WHERE branchid='"+branchid+"'";

                    try
                    {
                        connection.Open();
                        command = new SqlCommand(str, connection);
                        SqlDataReader dr1 = command.ExecuteReader();
                        connection.Close();
                        disp_grid();
                        MessageBox.Show("ระบบอัพเดทข้อมูลเรียบร้อยแล้ว (save is successful++)");
                        btncancel.Enabled = false;
                        btn_save.Enabled = false;
                        panelBranch.Enabled = false;
                        state = 0;
                    }
                    catch (SqlException ex)
                    {
                        MessageBox.Show(ex.ToString());
                    }
                }


            }
        }

        private void cboClassid_SelectedIndexChanged(object sender, EventArgs e)
        {
             classid = ds.Tables["class"].Rows[cboClassid.SelectedIndex]["classid"].ToString();
        }
  
        private void btndel_Click(object sender, EventArgs e)
        {
            if (MessageBox.Show("Are you sure want to delete this branch ?", "Messsage", MessageBoxButtons.YesNo, MessageBoxIcon.Question) == DialogResult.Yes)
            {

                int rowindex = dataGridView1.CurrentRow.Index;
                string branch = dataGridView1.Rows[rowindex].Cells[0].Value.ToString();
                SqlConnection connection = misdb.MISMsSqlConnect("172.18.0.53", "in-house", "foxuser", "foxpro");
                string str = "DELETE FROM dbo.branchdetail WHERE branchid='" + branch + "'";
                try
                {
                    connection.Open();
                    command = new SqlCommand(str, connection);
                    SqlDataReader dr1 = command.ExecuteReader();
                    connection.Close();
                    disp_grid();
                    MessageBox.Show("ระบบลบข้อมูลเรียบร้อยแล้ว (Delete is successful++)");
                }
                catch (SqlException ex)
                {
                    MessageBox.Show(ex.ToString());
                }

            }

        }

        private void dataGridView1_DoubleClick(object sender, EventArgs e)
        {
            int rowindex = dataGridView1.CurrentRow.Index;
            string branch = dataGridView1.Rows[rowindex].Cells[0].Value.ToString();

            txtBranchid.Text = dataGridView1.Rows[rowindex].Cells[0].Value.ToString();
            txtBranchname.Text = dataGridView1.Rows[rowindex].Cells[1].Value.ToString();
            txtShotname.Text = dataGridView1.Rows[rowindex].Cells[2].Value.ToString();
            
            txtZone.Text = dataGridView1.Rows[rowindex].Cells[3].Value.ToString();
            cboClassid.SelectedValue = dataGridView1.Rows[rowindex].Cells[4].Value.ToString();
            txtRoom_id.Text = dataGridView1.Rows[rowindex].Cells[5].Value.ToString();
            txtAreaid.Text = dataGridView1.Rows[rowindex].Cells[6].Value.ToString();
            txtTotalarea.Text = dataGridView1.Rows[rowindex].Cells[7].Value.ToString();
            txtUse_area.Text = dataGridView1.Rows[rowindex].Cells[8].Value.ToString();
            txtStock_area.Text = dataGridView1.Rows[rowindex].Cells[9].Value.ToString();
            txtRoom_number.Text = dataGridView1.Rows[rowindex].Cells[10].Value.ToString();

           // dtOpendate.Format = DateTimePickerFormat.Short;

            DateTime dtBookPublishDate = DateTime.Parse(dataGridView1.Rows[rowindex].Cells[11].Value.ToString());
            dtOpendate.Value = DateTime.Parse(dtBookPublishDate.ToShortDateString());

            txtAddress1.Text = dataGridView1.Rows[rowindex].Cells[12].Value.ToString();
            txtAddress2.Text = dataGridView1.Rows[rowindex].Cells[13].Value.ToString();
            txtTumbol.Text = dataGridView1.Rows[rowindex].Cells[14].Value.ToString();
            txtAumper.Text = dataGridView1.Rows[rowindex].Cells[15].Value.ToString();
            txtProvince.Text = dataGridView1.Rows[rowindex].Cells[16].Value.ToString();
            txtZipcode.Text = dataGridView1.Rows[rowindex].Cells[17].Value.ToString();
            txtTel01.Text = dataGridView1.Rows[rowindex].Cells[18].Value.ToString();
            txtTel02.Text = dataGridView1.Rows[rowindex].Cells[19].Value.ToString();
            txtTel03.Text = dataGridView1.Rows[rowindex].Cells[20].Value.ToString();
            txtManagername.Text = dataGridView1.Rows[rowindex].Cells[22].Value.ToString();
            txtEmployees_number.Text = dataGridView1.Rows[rowindex].Cells[23].Value.ToString();


        }

        private void clearTextbox() {
            txtBranchid.Text = "";
            txtBranchname.Text = "";
            txtShotname.Text = "";
            txtZone.Text = "";
            txtRoom_id.Text = "";
            txtAreaid.Text = "";
            txtTotalarea.Text = "";
            txtUse_area.Text = "";
            txtStock_area.Text = "";
            txtRoom_number.Text = "";
            txtAddress1.Text = "";
            txtAddress2.Text = "";
            txtTumbol.Text = "";
            txtAumper.Text = "";
            txtProvince.Text = "";
            txtZipcode.Text = "";
            txtTel01.Text = "";
            txtTel02.Text = "";
            txtTel03.Text = "";
            txtManagername.Text = "";
            txtEmployees_number.Text = "";
            dtOpendate.Value = DateTime.Today;
            cboClassid.SelectedValue = 1;
        }

        private void btnedit_Click(object sender, EventArgs e)
        {
            state = 2;
            panelBranch.Enabled = true;
            btncancel.Enabled = true;
            btn_save.Enabled = true;

        }

        private void metroLabel9_Click(object sender, EventArgs e)
        {

        }
    }
}
