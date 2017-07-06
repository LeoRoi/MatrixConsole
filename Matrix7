package b1_557966;

/**
 * Matrix class with all requierd methods
 * https://rechneronline.de/lineare-algebra/matrizen.php
 * @author 55-79-66
 *
 */

import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

class Matrix7 {
	
	private int r, c;
	private float[][] ma;

	/**
	 * matrix constructor 
	 * @param test allows to run internal tests with specific matrices if set to !0
	 */
	Matrix7(int test) {
		
		if(test == 0) {
			System.out.print("\nmatrix-rows: ");
			r = intCheck(1, 7);
			System.out.print("matrix-columns: ");
			c = intCheck(1, 7);		
			ma = new float[r][c];
			
			System.out.println("Care to fill matrix with random elements? - 0 / 1");
			int random = intCheck(0, 1);
			if(random == 1) {
				for(int i = 0; i < r; i++) for(int j = 0; j < c; j++) ma[i][j] = (float)(-99 + Math.random() * 198);
			}
			else {
				System.out.println("enter matrix-elements row for row: ");
				for(int i = 0; i < r; i++) for(int j = 0; j < c; j++) ma[i][j] = floatCheck(-99, 99);
				System.out.println("Matrix successfully created!");
			}
		}	
		else {
			r = 4; 
			c = 5;
			ma = new float[][] { {1.0f, -1.0f, 2.0f, 1.0f, 3.0f},
								{-2.0f, 2.0f, 0.0f, 4.0f, -6.0f},
								{-1.0f, 1.0f, 2.0f, 5.0f, -3.0f},
								{0.0f, 1.0f, 3.0f, -5.0f, 1.0f} };
		}
	}
	
	/**
	 * constructor, mainly for m3-result matrix
	 * @param row
	 * @param col
	 */
	Matrix7(int row, int col) {
		r = row;
		c = col;
		ma = new float[r][c];
	}
	
	/**
	 * check wheter or not a matrix exists
	 * @param ind index of matrix in an array
	 * @param m array with Matrix7 objects
	 */
	static void exCheck(int ind, Matrix7[] m) {
		if(m[ind] == null) {
			System.out.printf("\nCannot proceed because m%d does not exist!\n", ind + 1);
			Matrix7_demo.menu(m);
		}		
	}

	
	/**
	 * display matrix with index X
	 * @param ind
	 * @param m
	 */
	static void output(int ind, Matrix7[] m) {
		
		if(m[ind] != null) {
			
			System.out.printf("\n<m%d> with %d rows & %d columns:\n", ind + 1, m[ind].r, m[ind].c);		
			for(int i = 0; i < m[ind].r; i++) {
				for(int j = 0; j < m[ind].c; j++) System.out.printf("%10.2f\t", m[ind].ma[i][j]);
				System.out.println();
			}
		}
		else System.out.printf("\nMatrix <m%d> does not exist!\n", ind + 1);
	}

	/**
	 * copy m1 content to m3
	 * @param m
	 */
	static void copy(Matrix7[] m){
		
		m[2] = new Matrix7(m[0].r, m[0].c);
        for(int i = 0; i < m[0].r; i++) for(int j = 0; j < m[0].c; j++) m[2].ma[i][j] = m[0].ma[i][j];
	}
	
	
	/**
	 * computate the rank of a matrix
	 * @param m
	 */
	static void rank(Matrix7[] m) {
		
		exCheck(0, m);		
		copy(m);		
		int rank = m[2].c;
		int r = m[2].r;
		
		for(int row = 0; row < rank; row++) {
			
	        // diagonal element !0
	        if(row < r && m[2].ma[row][row] != 0){
	           for(int col = 0; col < r; col++){
	               if(col != row){
	                 double mult = (double) m[2].ma[col][row] / m[2].ma[row][row];
	                 for(int i = 0; i < rank; i++) m[2].ma[col][i] -= mult * m[2].ma[row][i];
	              }
	           }
	        }
	        else{
	            boolean reduce = true;
	 
	            // !0 element search (current column)
	            for(int i = row + 1; i < r;  i++){
	                // swap the row with non-zero element and this row
	                if(m[2].ma[i][row] != 0){
	                	for(int j = 0; j < rank; j++){
	                        float temp = m[2].ma[row][j];
	                        m[2].ma[row][j] = m[2].ma[i][j];
	                        m[2].ma[i][j] = temp;
	                    }
	                    reduce = false;
	                    break ;
	                }
	            }
	           
	            if(reduce){
	                rank--;
	                // last column-copy
	                for(int i = 0; i < r; i ++) m[2].ma[i][row] = m[2].ma[i][rank];
	            }	 
	            row--;
	        }
	    }
		System.out.printf("\nRank of the matrix is: %d\n", rank); 
	}

	
	/**
	 * find the row with the biggest sum
	 * @param m
	 */
	static void bigRow(Matrix7[] m) {
		exCheck(0, m);

		float temp = 0, big = 0;
		for (int i = 0; i < m[0].r; i++) {
			for (int j = 0; j < m[0].c; j++) temp += m[0].ma[i][j];
			if (temp > big) {
				big = temp;
			}
			temp = 0;
		}
		System.out.printf("\nThe sum of the biggest row is %.2f\n", big);
	}

	/**
	 * transpose m1
	 * @param m
	 */
	static void transpose(Matrix7[] m) {
		exCheck(0, m);

		m[2] = new Matrix7(m[0].c, m[0].r);
		for (int i = 0; i < m[0].r; i++) {
			for (int j = 0; j < m[0].c; j++) {
				m[2].ma[j][i] = m[0].ma[i][j];
			}
		}
		output(2, m);
	}
	
	
	/**
	 * matrix multiplication
	 * @param m
	 */
	static void mult(Matrix7[] m) {
		exCheck(0, m);
		exCheck(1, m);
				
		if(m[0].c == m[1].r) {
			
			System.out.printf("\nm1 * m2:\n");
			int ra = m[0].r; //row a
			int ca = m[0].c; //column a
			int cb = m[1].c; //column b
			m[2] = new Matrix7(ra, cb);
			
			for(int i = 0; i < ra; i++) { //row a
				for(int j = 0; j < cb; j++) { //column b
					for(int k = 0; k < ca; k++) m[2].ma[i][j] += (m[0].ma[i][k] * m[1].ma[k][j]); //column a = row b
				}
			}
			output(2, m);
		}
		else System.out.println("\nm1 & m2 are unequal — operation impossible!");
	}
	
	/**
	 * scalar multiplication with float k in range [-99, 99]
	 * @param m
	 */
	static void scaMul(Matrix7[] m) {
		
		exCheck(0, m);
		System.out.print("\nfaktor k? I = [-99; 99]");
		float k = floatCheck(-99, 99);
		m[2] = new Matrix7(m[0].r, m[0].c);
		System.out.printf("\nMatrix * %.2f:\n", k);
		for(int i = 0; i < m[0].r; i++) {
			for(int j = 0; j < m[0].c; j++) m[2].ma[i][j] = m[0].ma[i][j] * k;
		}
		output(2, m);
	}

	/**
	 * matrix addition 
	 * @param m
	 */
	static void addition(Matrix7[] m) {
		exCheck(0, m);
		exCheck(1, m);

		if (m[0].r == m[1].r && m[0].c == m[1].c) {
			m[2] = new Matrix7(m[0].r, m[0].c);
			System.out.println("\nm1 + m2:");
			for (int i = 0; i < m[0].r; i++)
				for (int j = 0; j < m[0].c; j++) m[2].ma[i][j] = m[0].ma[i][j] + m[1].ma[i][j];
			output(2, m);
		} else
			System.out.println("\nm1 & m2 are unequal — operation impossible!");

	}
	
	/**
	 * check if the user input is between bounds and has float typ	 * 
	 * @param lowerBound
	 * @param upperBound
	 * @return
	 */
	static float floatCheck(int lowerBound, int upperBound) {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		float temp = 0;
		String in;
		boolean loop;

		do {
			try {
				loop = false;
				in = br.readLine();
				temp = Float.parseFloat(in);

				if (temp < lowerBound) {
					System.out.println("Only positive numbers are allowed!");
					loop = true;
				}
				if (temp > upperBound) {
					System.out.printf("The biggest allowed number is %d!", upperBound);
					loop = true;
				}
			}

			catch (NumberFormatException nfe) {
				System.out.println("Please enter a number!");
				loop = true;
			} catch (IOException ioe) {
				loop = true;
				System.out.println("Input error!");
			}

		} while (loop);
		return temp;
	}
	
	
	/**
	 * check if the user input is between bounds and has int typ	 * 
	 * @param lowerBound
	 * @param upperBound
	 * @return
	 */
	static int intCheck(int lowerBound, int upperBound) {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int temp = 0;
		String in;
		boolean loop;

		do {
			try {
				loop = false;
				in = br.readLine();
				temp = Integer.parseInt(in);

				if (temp < lowerBound) {
					System.out.println("Only positive numbers are allowed!");
					loop = true;
				}
				if (temp > upperBound) {
					System.out.printf("The biggest allowed number is %d!\n", upperBound);
					loop = true;
				}
			}

			catch (NumberFormatException nfe) {
				System.out.println("Please enter a number!");
				loop = true;
			} catch (IOException ioe) {
				loop = true;
				System.out.println("Input error!");
			}

		} while (loop);
		return temp;
	}
}
