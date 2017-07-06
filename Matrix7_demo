package b1_557966;

public class Matrix7_demo {	 
	public static void main(String[] args) {
		
		System.out.println("\nWelcome to matrix calculator!\n");
		Matrix7[] m = new Matrix7[3];
        menu(m);
        System.out.println("\nProgram will be closed.\nSo long!");
	}
	
	static void menu(Matrix7[] m) {        
        int select;        
        do {
	        System.out.println("\nMenu\n");
	        System.out.printf(" 0 EXIT\n"
	                + " 1 compose matrix one (m1)\n"
	                + " 2 compose matrix two (m2)\n"
	                + " 3 show saved matrices\n"
	                + " 4 m1 + m2\n"
	                + " 5 m1 * m2\n"
	                + " 6 k * m1 (scalar multiplication)\n"
	                + " 7 the transpose of m1\n"
	                + " 8 the rank of m1\n"
	                + " 9 biggest row m1\n"
	                + "10 show last result (m3)\n"
	                + "_________________________________\n"
	                + "your choice >> ");
	        
	        select = Matrix7.intCheck(0, 10);        
	        switch(select) {
	        
	            case 0:                    
	                break;
	            
	            case 1:
	                m[0] = new Matrix7(0);
	                Matrix7.output(0, m);
	                break;
	                
	            case 2:
	            	m[1] = new Matrix7(0);
	                Matrix7.output(1, m);
	                break;
	                
	            case 3:
	                Matrix7.output(0, m);
	            	Matrix7.output(1, m);
	                break;
	                
	            case 4:
	            	Matrix7.addition(m);
	                break;
	                
	            case 5:
	            	Matrix7.mult(m);
	                break;
	            
	            case 6:
	            	Matrix7.scaMul(m);
	                break;
	                
	            case 7:
	            	Matrix7.transpose(m);
	                break;
	                
	            case 8:
	            	Matrix7.rank(m);
	                break;
	                
	            case 9:
	            	Matrix7.bigRow(m);
	                break;
	                
	            case 10:
	            	Matrix7.output(2, m);
	                break;
	                
	            case 11:
	            	Matrix7.output(2, m);
	                break;    
	            
	        }
        } while (select != 0);
    }
}
