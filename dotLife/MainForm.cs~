using System;
using System.Windows.Forms;
using System.Drawing;

namespace dotLife
{
	public class MainForm:Form
	{
		Timer timer=new Timer ();
		MainMenu mainMenu=new MainMenu();
		StatusBar status = new StatusBar ();
		Label info=new Label ();
		Life life =new Life ();
		public MainForm ()
		{
			Size = new Size (640, 640);
			StartPosition = FormStartPosition.CenterScreen;
			Text = "Игра \"Жизнь\"";
			mainMenu.MenuItems.Add(new MenuItem("Start",StartLife));
			mainMenu.MenuItems.Add(new MenuItem("Pause",PauseLife));
			mainMenu.MenuItems.Add(new MenuItem("Stop",StopLife));
			timer.Interval = 1000;
			timer.Tick += Step;
			this.Menu = mainMenu;
			Controls.Add (status);
			status.Controls.Add (info);
			info.AutoSize = true;
			DisplayInfo ();
		}
		public void StopLife(Object sender,EventArgs e){
			timer.Stop ();
			life = new Life ();
			this.Invalidate ();
		}
		public void StartLife(Object sender,EventArgs e){
				timer.Start ();
		}
		public void PauseLife(Object sender,EventArgs e){
			timer.Stop ();
		}
	protected override void OnPaint (PaintEventArgs e)
		{
			base.OnPaint (e);

			Graphics g = this.CreateGraphics();
			g.Clear (SystemColors.Info);
			for (int i = 0; i <= Life.W; i++){

				g.DrawLine (Pens.Black, 0, i * (this.Height / Life.W),
					this.Width , i  * (this.Height / Life.W));
				g.DrawLine (Pens.Black,  i * (this.Width  / Life.W),0
					, i  * (this.Width  / Life.W),this.Height);
				
			}
			for (int i = 0; i < Life.W; i++)
				for (int j = 0; j < Life.W; j++) {
					if (life.Cells [i, j].Current) {
						float x = i * (this.Width / Life.W);
						float y = j * (this.Height / Life.W);
						g.FillRectangle (Brushes.Green, new RectangleF (
							x+1,y+1,
							 (this.Width  / Life.W)-1, (this.Height / Life.W)-1
						));
					}
				}
		}
		public void DisplayInfo(){
			info.Text = $"Gen = {life.Gen}; Cells= {life.Count}; Alive ={life.Alive}; ";
		}
		public void Step(object o,EventArgs e){
			
			life.NextGen ();
			DisplayInfo ();
			this.Invalidate ();

			if (life.Alive <= 0) {
				timer.Stop ();
			
				MessageBox.Show ("The End");
			}
		}
	}
}

