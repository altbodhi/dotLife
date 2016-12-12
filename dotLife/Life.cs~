using System;

namespace dotLife
{
	public class Life
	{
		public static int W = 32;
		public static int MAX=100;
		public int Gen{ get; set; }

		Cell[,] cells = null;
		Random rnd = new Random (DateTime.Now.Millisecond);

		public bool NextRnd{ get { return rnd.Next (100) < 50; } }

		public Life ()
		{
			
			Life.W = 100;
			cells = new Cell[W, W];
			Gen = 1;
			int total = 0;
			for (int i = 0; i < W; i++) {
				if (total >= MAX)
					break;
				for (int j = 0; j < W; j++) {
					cells [i, j] = new Cell (NextRnd, false);
					if (cells [i, j].Current)
						//total++;
					if (total >= MAX)
						break;
				}
			}
		}

		bool isBorn (int i, int j)
		{
			int count = 0;
			for (int a = i - 1; a < i - 1 + 3; a++) {
				if (a < 0)
					continue;
				if (a >= W)
					continue;
				for (int b = j - 1; b < j - 1 + 3; b++) {
					if (b < 0)
						continue;
					if (b >= W)
						continue;
					if (a == i && b == j)
						continue;
					if (cells [a, b].Current)
						count++;
				
				}
			}
			return count == 3;
		}
		bool isAlive (int i, int j)
		{
			int count = 0;
			for (int a = i - 1; a < i - 1 + 3; a++) {
				if (a < 0)
					continue;
				if (a >= W)
					continue;
				for (int b = j - 1; b < j - 1 + 3; b++) {
					if (b < 0)
						continue;
					if (b >= W)
						continue;
					if (a == i && b == j)
						continue;
					if (cells [a, b].Current)
						count++;

				}
			}
			if ((count == 3)||
				(count ==2))
				return true;
				else
			return false;
		}
		public void NextGen ()
		{
			
			for (int i = 0; i < W; i++)
				for (int j = 0; j < W; j++) {
					if (!cells [i, j].Current) {
						cells [i, j].Next = isBorn (i, j);
					}
					if (cells [i, j].Current) {
						cells [i, j].Next = isAlive (i, j);
					}
				}
			for (int i = 0; i < W; i++)
				for (int j = 0; j < W; j++) {
					cells [i, j].Current = cells [i, j].Next;
					cells [i, j].Next = false;
				}
			Gen++;
		}

		public Cell[,] Cells{ get { return cells; } }

		public int Count{get{return W*W;}}

		public int Alive{
			get{ 
				int c = 0;
				for (int i = 0; i < W; i++)
					for (int j = 0; j < W; j++) 
						if (cells [i, j].Current)
							c++;
					
				return c;	
			}
		}
	}
}

