import java.util.*;
import java.util.Scanner;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;

interface Database{

	void deposit(int Amount);
	void withdraw(int Amount);
	void balance();
}
abstract class Abstraction
{
	int amount;
	abstract void transfer(Account receiver,int amount);
	abstract void printAccountDetails();
}
class Account{

	protected long balance;
	protected String name;
	protected String Account_Type;
	protected int PIN;
    protected long Account_No;

	static{
		System.out.println("Account Creation has been initiated..");
	}

	void createAccount(){

		Scanner sc = new Scanner(System.in);
		int pin1,pin2,suffix;
		System.out.print("Enter Name:");
		name = sc.nextLine();
		System.out.print("Enter Bank Account Type:");
		Account_Type = sc.nextLine();

		do{
			do{
				System.out.print("Enter a four-digit PIN:");
				pin1 = sc.nextInt();
				if(pin1<=999 || pin1>=10000){
					System.out.println("Invalid Please Enter a PIN containing 4 digits");
				}
			}while(pin1<=999|| pin1>=10000);

			System.out.print("Re-Enter to Confirm:");
			pin2 = sc.nextInt();

			if(pin1!=pin2){
				System.out.println("Entered PIN doesn't match\nRetry...");
			}

		}while(pin1!=pin2);

		System.out.println("PIN set Successful");
		PIN = pin1;
		System.out.print("Deposit Opening Balance..");
		do{
			System.out.println("(Please make sure that opening balance is Greater than or Equal to Rs.1000)");
		    balance = sc.nextLong();
		}while(balance<1000);

		System.out.println("Deposit Successful");
		System.out.println("---------------------------");
		System.out.println("Account Creation Successful");
		System.out.println("---------------------------");

		Random r = new Random();
		Account_No = r.nextLong(1000000000000000L,9999999999999999L);
		System.out.println("Your Assigned Account Number:"+Account_No);

	}//end of method createAccount

	Account getReference(){
		return this;
	}

}//end of class Account

class Transactions extends Abstraction implements Database{

	private Account ref;

	Transactions(Account ref){
		this.ref = ref;
	}

	public void deposit(int d){
		ref.balance = ref.balance+d;
		System.out.println("Rs."+d+" Deposit Successful");
    }


	public  void withdraw(int w){

		if(ref.balance-w < 0){
			System.out.println("Requested Ammount Cannot be Withdrawn");
			System.out.println("Insufficient Balance..");
			return;
		}

		ref.balance = ref.balance-w;
	    System.out.println("Rs."+w+" Withdraw Successful");
    }

	public  void withdraw(int no_of_notes, int denomination){
	    int w = no_of_notes*denomination;

		if(ref.balance-w < 0){
			System.out.println("Requested Ammount Cannot be Withdrawn");
			System.out.println("Insufficient Balance..");
			return;
		}

		ref.balance = ref.balance-w;
	    System.out.println("Rs."+w+" Withdraw Successful");
    }


	public void balance(){
		System.out.println("Available Bank Balance:"+ref.balance);
	}

	void transfer(Account receiver,int amount){
		
		super.amount = amount;

		if(ref.balance-super.amount < 0){
			System.out.println("Insufficient Balance..");
		}

		ref.balance = ref.balance-super.amount;
		receiver.balance = receiver.balance+super.amount;
		System.out.println("Transfer Successful...");
	}

	void printAccountDetails(){
		System.out.println("-------------------------------------------------------");
        System.out.println("Account Details:");
        System.out.println("Name: " + ref.name);
        System.out.println("Account Type: " + ref.Account_Type);
        System.out.println("Account Number: " + ref.Account_No);
        System.out.println("Balance: " + ref.balance);
		System.out.println("-------------------------------------------------------");
    }
}

class BankingManagement
{
	@SuppressWarnings("removal")
	public static void main(String[] args)throws InputMismatchException
	{
		try {
			Scanner sc = new Scanner(System.in);
			long accno,transAccNo;
			int idx=-1,idx2=-1,pin,deposit,withdraw,transferAmmount,noOfNotes,denomination;
			boolean flag;
			System.out.print("Enter the number of Accounts to Create:");
			int n = sc.nextInt();
			Account[] a = new Account[n];

			for(int i=0;i<n;i++){
				System.out.println("-------------------------------");
				System.out.println("Enter the details for Account "+(i+1));
				System.out.println("-------------------------------");
				a[i] = new Account();
				a[i].createAccount();
			}

			System.out.println("---------------------------------------------------Loading----------------------------------------------------------");
			
			xyz:while(true){			   //while 1
				System.out.print("Enter Your Account Number:");
				accno = sc.nextLong();
				flag = false;

				for(int i=0;i<n;i++){
					if(accno == a[i].Account_No){
						idx = i;
						flag = true;
						break;
					}
				}

				if(flag == false){
					System.out.println("Account Number doesn't exist.....");
					continue;
				}

				else{
					System.out.print("Enter your pin:");
					pin = sc.nextInt();
					if(pin != a[idx].PIN){
						System.out.println("---------------\nIncorrect Pin\n---------------");
						System.out.println("Try Again Later......");
						continue;
					}
					System.out.println("---------------------------------------------------Loading----------------------------------------------------------");
					System.out.println("Account accessed...");
				}

				abc:while(true){				//while 2
					System.out.println("1.Deposit\n2.Withdrwal\n3.Withdrawl(Denomination)\n4.Transfer\n5.Balance\n6.Receipt\n7.Close Account\n8.Close Bank");
					System.out.println("-------------------------------");
					System.out.print("Choose the option:");
					int ch = sc.nextInt();
					Account ref = a[idx].getReference();
					Transactions t = new Transactions(ref);

					switch(ch){
						case 1:
							System.out.print("Enter the amount to deposit:");
							deposit = sc.nextInt();
							t.deposit(deposit);
							break;
						case 2:
							System.out.print("Enter the amount to withdraw:");
							withdraw = sc.nextInt();
							t.withdraw(withdraw);
							break;
						case 3:
							System.out.print("Enter Number of notes:");
							noOfNotes = sc.nextInt();
							System.out.print("Enter the Denomination:");
							denomination = sc.nextInt();
							t.withdraw(noOfNotes,denomination);
							break;
						case 4:
							System.out.print("Enter the Account Number to transfer:");
							transAccNo = sc.nextLong();
							flag = false;
							for(int i=0;i<n;i++){
								if(transAccNo == a[i].Account_No){
									idx2 = i;
									flag = true;
									break;
								}
							}
							if(flag == true){
								System.out.print("Enter the amount to transfer:");
								transferAmmount = sc.nextInt();
								t.transfer(a[idx2],transferAmmount);
							}
							else{
								System.out.println("Entered Account number doesn't exist....");
							}
							break;
						case 5:
							t.balance();
							break;
						case 6:
							t.printAccountDetails();
							break;
						case 7:
							System.out.println("ThankYou for banking with us..");
							break abc;
						case 8:
							break xyz;
						default:
							System.out.println("Invalid choice....");
							break;
					}//end of switch
				}//end of while2
			}//end of while1 
			BankingManagement ob = new BankingManagement();
			ob.finalize();
		}
		catch (InputMismatchException e){
			System.out.println("Invalid input. Please enter a valid number.");
		}
		finally{
			System.out.println("Banking Portal has been Closed..");
			JFrame frame = new JFrame();
			  frame.setSize(500, 200);
              JPanel panel = new JPanel();
              JButton label = new JButton("Thank you for Banking with us ! ");
              panel.add(label);
              frame.add(panel);
              frame.setVisible(true);
		}
	}// end of main	
	@Override
		public void finalize() throws Throwable{
		try{
			System.out.println("Finalize() method is called");
		}catch(Throwable th){
			throw th;
		}
		finally{
			super.finalize();
		}
	}
}//end of class