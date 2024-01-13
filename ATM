import java.util.*;
import java.util.concurrent.TimeUnit;
public class ATM
{
    static String userName="Charan"; // Considering A Sample Credentials... A List Of Credentials Are Present In Big DataBase Management System
    static String passKey="13135"; // Considering A Sample Credentials... A List Of Credentials Are Present In Big DataBase Management System
	public static void main(String[] args) throws InterruptedException {
	    Scanner sc=new Scanner(System.in);
	    int attempts=0;
	    System.out.println("--------------------------- Welcome To ATM Interface -----------------------"); // User Interface
	    System.out.println("----------- To Access Our ATM Services You Need To Authenticate Your Credentials ---------"); // User Interface
	    System.out.println("Please Enter Your UserName: "); 
	    String cn=sc.next(); //Input UserName
	    System.out.println("Please Enter Your Password"); 
	    String cp=sc.next(); //Input PassWord
	    try{
	    boolean ans=authenticate(cn,cp,userName,passKey,attempts); // calling authenticate method 
	    if(ans==true) // if authentication done successfully then it will be redirected to HomePage to unlock the ATM services
	    {
	        HomePage(); // calling method
	    }
	    }
	    catch(InterruptedException e)
	    {
	        System.out.println("InterruptedException Caught...");
	        e.printStackTrace();
	    }
	    return;
	}
	public static boolean authenticate(String cn,String cp,String userName,String passKey,int attempts) throws InterruptedException
	{
	    Scanner sc=new Scanner(System.in);
	    if(cn.equalsIgnoreCase(userName) && cp.equalsIgnoreCase(passKey)) // Checking whether User Details are Valid Or Not
	    {
	        System.out.println("Credentials Verified Successful...");
	        TimeUnit.SECONDS.sleep(1); // sleep for 1 second to display the above message
	        return true;
	    }
	    else{
	        attempts++;
	        final int FIXED_ATTEMPTS=3;
	        if(attempts<=FIXED_ATTEMPTS) { // giving 3 attempts for user to enter a valid credentials
	        System.out.println("Access Denied Due to \"INVALID CREDENTIALS\". Please Enter Valid Credentials To Access Our ATM Services");
	        String c_n=sc.next(); //Taking userName as Input Again For sake of User to Enter Valid UserName
	        String c_p=sc.next(); //Taking passkey as Input Again For sake of user to Enter Valid Password
	        authenticate(c_n,c_p,userName,passKey,attempts);// calling authenticate within the method
	        }
	        else{
	            System.out.println("Number Of Attempts Limit Exceeded! Please try again after an hour");
	        }
	        return false;// return to main method if attempts limit exceeded
	    }
	}
	public static void HomePage()
	{
	    System.out.println("-------------------------Welcome To HomePage-------------------------------");
	    System.out.println("---------------->>>>> Here Are The List Of Our Services Please Select Your Choice<<<<--------------");
	    System.out.println("1)Deposit\n2)Withdraw\n3)TransactionHistory\n4)Transfer\n5)Quit");
	    Scanner sc=new Scanner(System.in);
	    int choice=sc.nextInt();
	    switch(choice)
	    {
	        case 1: ATM.Deposit d=new ATM.Deposit();
	                try{
	                d.DepositIntoBank(); // invoking DepositIntoBank() Method 
	                }
	                catch(InterruptedException C)
	                {
	                    System.out.println("InterruptedException Caught...");
	                    C.printStackTrace();
	                }
	                break;
	        case 2: ATM.Withdraw w=new ATM.Withdraw();
	                try{
	                w.WithdrawFromBank(); // invoking WithdrawFromBank() Method
	                }
	                catch(InterruptedException c)
	                {
	                    System.out.println("InterruptedException Caught...");
	                    c.printStackTrace();
	                }
	                break;
	        case 3: ATM.TransactionHistory T_H=new ATM.TransactionHistory();
	                try{
	                T_H.TransactionHistoryFromAccount();// invoking TransactionHistoryFromAccount() Method
	                }
	                catch(InterruptedException a)
	                {
	                    System.out.println("InterruptedException Caught...");
	                    a.printStackTrace();
	                }
	                break;
	        case 4: ATM.Transfer t=new ATM.Transfer();
	                try{
	                t.TransferToAccount(); //invoking TransferToAccount() Method
	                }
	                catch(InterruptedException s)
	                {
	                    System.out.println("InterruptedException Caught...");
	                    s.printStackTrace();
	                }
	                break;
	        case 5: ATM.Quit q=new ATM.Quit();
	                try{
	                q.QuitFromAtm(); // invoking QuitFromAtm() method
	                }
	                catch(InterruptedException l)
	                {
	                    System.out.println("InterruptedException Caught...");
	                    l.printStackTrace();
	                }
	                break;
	        default: System.out.println("Entered Invalid Choice....Please select valid one..");
	    }
	}
	static double balance=0;// initial consideration as 0 bank balance
	static String TransactionHistory=""; // TransactionHistory String to maintain the debits & credits history within user account
	static class Deposit
	{
	    void DepositIntoBank() throws InterruptedException // exception handling using throws Keyword
	    {
	        Scanner sc=new Scanner(System.in);
	        System.out.println("How Much Amount You Wish To Deposit:");
	        double amount=sc.nextDouble();
	        System.out.println("Enter Your Pin");
	        String pin=sc.next();
	        balance=balance+amount;// updating balance in account
	        TransactionHistory=TransactionHistory+"Amount Deposited: "+amount+"\n"; //Updating TransactionHistory 
	        System.out.println("Amount Deposited Successfully...");
	        System.out.println("Current Balance: "+balance); // Printing The Current Balance
	        TimeUnit.SECONDS.sleep(1); // making method to sleep for 3 seconds 
	        ATM.HomePage();// Calling HomePage() method
	    }
	}
	static class Withdraw
	{
	    void WithdrawFromBank() throws InterruptedException
	    {
	        Scanner sc=new Scanner(System.in);
	        System.out.println("How Much Amount You Wish To Withdraw:");
	        double amount=sc.nextDouble();
	        System.out.println("Enter Your Pin");
	        String pin=sc.next();
	        if(amount<=balance) // checking if amount<balance
	        {
	            balance=balance-amount;// updating balance in account
	            TransactionHistory=TransactionHistory+"Amount Withdraw: "+amount+"\n";// updating TransactionHistory String
	            System.out.println("Amount Withdrawn Successfully...Please Collect The Cash");
	            System.out.println("Current Balance: "+balance);
	        }
	        else{
	            System.out.println("Insufficient Balance");
	        }
	        TimeUnit.SECONDS.sleep(1); //making method to sleep for 3 sec
	        ATM.HomePage(); // calling HomePage() method
	    }
	}
	static class TransactionHistory
	{
	    void TransactionHistoryFromAccount() throws InterruptedException
	    {
	        System.out.println(TransactionHistory); // Printing TransactionHistory string
	        TimeUnit.SECONDS.sleep(1);// making method to sleep for 3 seconds
	        ATM.HomePage(); // calling HomePage() method
	    }
	    
	}
	static class Transfer
	{
	    void TransferToAccount() throws InterruptedException
	    {
	        Scanner sc=new Scanner(System.in);
	        System.out.println("Enter Sender's Account number:");
	        String a_no=sc.next();
	        System.out.println("Enter Amount To Be Send");
	        double amount=sc.nextDouble();
	        if(amount<=balance) //checking if amount<= balance
	        {
	            System.out.println("Amount Transfered Successfully...");
	            balance=balance-amount;// updating balance
	            TransactionHistory=TransactionHistory+amount+" Transfered To: "+a_no+" Account ";//updating TransactionHistory
	            System.out.println("Current Balance: "+balance);
	        }
	        else{
	            System.out.println("Insufficient Balance...");
	        }
	        TimeUnit.SECONDS.sleep(1);// making method to sleep for 3 seconds
	        ATM.HomePage(); // calling HomePage() Mehtod
	    }
	}
	static class Quit
	{
	    void QuitFromAtm() throws InterruptedException
	    {
	        System.out.println("Thanks For Visiting Our ATM");// USER QUITS FOM QuitFromAtm() method
	    }
	}
}
