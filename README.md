# Tour_tourisam_mangment_system
A java project that includes all activities of a travel agency, including tour package management, online bookings, payments, and customer management


import java.util.Scanner;
class Main
{
    public static void main(String[] args)
    {
        Scanner sc=new Scanner(System.in);
        Main main=new Main();
        SL sl=new SL();

        System.out.println("\n=====================================");
        System.out.println("    Tour Management System          ");
        System.out.println("=====================================");
        System.out.println(" Welcome to Enough Tours & Travels");
        System.out.println("-------------------------------------");
        System.out.println("1.Sign-up");
        System.out.println("2.Login");
        System.out.println("3.Exit");
        System.out.print("Choice(1-3): ");
        int choice=sc.nextInt();
        sc.nextLine();

        switch(choice)
        {
            case 1:sl.Signup();break;
            case 2:sl.login();break;
            default:System.out.println("Invalid Choice,Try again");
        }
    }
}

class SL
{
    Scanner sc=new Scanner(System.in);
    String fn,pass;
    String loginpass;

    String Signup()
    {
        System.out.println("\n"+"             --------- ");
        System.out.println("              Sign-Up");
        System.out.println("             --------- "+"\n");

        System.out.print("       First Name:- ");
        fn=sc.nextLine();

        System.out.print("       Last Name:- ");
        String ln=sc.nextLine();

        int j=0;
        while(j<10)
        {
            System.out.print("       Email:- ");
            String email=sc.nextLine();
            String e=email;

            if(e.endsWith("@gmail.com"))
            {
                break;
            }
            else
            {
                System.out.println("       ==> Please Enter valid Email (eg:- xyz@gmail.com <==");
                j++;
            }
        }

        while(true)
        {
            System.out.print("       Generate Password:- ");
            pass=sc.nextLine();

            if(pass.length()==6)
            {
                break;
            }
            else
            {
                System.out.println("       ==> Password Length must be 6,Enter Again <==");
            }
        }

        int i=0;
        while(i<3)
        {
            System.out.print("       Confirm Password:- ");
            String pass2=sc.nextLine();

            if(pass.equals(pass2))
            {
                System.out.println("\n       ==> Sign-up Successfull,Please Login <==");
                login();
                break;
            }
            else
            {
                System.out.println("       ==> Incorrect!,Please Enter Again <==");
                i++;
            }
        }
        return pass;
    }

    void login()
    {
        System.out.println("\n"+"            -----------");
        System.out.println("             L O G I N ");
        System.out.println("            -----------"+"\n");

        int i=0;
        while(i<3)
        {
            System.out.print("       First Name:- ");
            String fnlogin=sc.nextLine();

            System.out.print("       Password:- ");
            loginpass=sc.nextLine();

            if(fn==null && pass==null)
            {
                System.out.println("       ==> No User Details Found,SignUp First <== ");
                Signup();
            }

            if(fnlogin.equals(fn))
            {
                loginp();
                break;
            }
            else
            {
                System.out.println("       ==> No Username Found Enter Again <==");
                i++;
                if(i==3)
                {
                    System.out.println("       ==> Maximum Attempts Reached,Try after a While <==");
                }
            }
        }
    }

    void loginp()
    {
        String pp=loginpass;
        int i=0;

        while(i<4)
        {
            if(pp.equals(pass))
            {
                System.out.println("\n---------------------------------------");
                System.out.println("  Welcome "+fn+", Lets Explore The World ");				
                System.out.println("---------------------------------------");

                Menu m=new Menu();
                m.options();
                break;
            }
            else
            {
                System.out.println("       ==> Incorrect Password,Try Again <==");
                i++;

                if(i==4)
                {
                    System.out.println("       ==> Maximum Attempts Reached,Try after a While <==");
                    break;
                }

                System.out.print("       Password:- ");
                pp=sc.nextLine();
            }
        }
    }
}

class Menu {
    Scanner sc = new Scanner(System.in);

    void options()
    {
        InternationalMenu im=new InternationalMenu();
        DomesticMenu dm=new DomesticMenu();

        while (true) {
            System.out.println(" -=Menu=-");
            System.out.println(" 1. International Tour Packages");
            System.out.println(" 2. Domestic Tour Packages");
            System.out.println(" 3. Sign-Out");
            System.out.print(" Enter Your Choice (1-3): ");
            int menuchoice1 = sc.nextInt();
            sc.nextLine();  // FIXED

            switch (menuchoice1)
            {
                case 1: im.options(); break;
                case 2: dm.options(); break;

                case 3:
                    System.out.println("\n Signing out... Returning to Main Menu.\n");
                    return;

                default:
                    System.out.println(" Invalid choice! Please enter a valid option.");
            }
        }
    }
}

class DomesticMenu
{
    Scanner sc = new Scanner(System.in);

    void options()
    {
        while(true)
        {
            System.out.println("\n --------------------------");
            System.out.println(" ==> Domestic Tour Packages");
            System.out.println("\n 1. View Packages");
            System.out.println(" 2. Buy Pachages");
            System.out.println(" 3. Go to previes page");
            System.out.print(" Enter Your Choice (1-3): ");

            int menuchoiceD = sc.nextInt();
            sc.nextLine(); // FIXED

            System.out.println("------------------------------------");

            switch (menuchoiceD)
            {
                case 1: new MainPackagesdomestic(); break;
                case 2: new buypackagedom(); break;
                case 3: return;

                default: System.out.println(" Invalid choice! Please enter a valid option.");
            }
        }
    }
}

class MainPackagesdomestic
{
    dpackagesdetail dpd[]=new dpackagesdetail[6];

    dpackages dp=new dpackages();

    MainPackagesdomestic()
    {
        dpd[0]=new dpackagesdetail(1,"Goa Bliss","Hotel Regent Laguna",3,27700);
        dpd[1]=new dpackagesdetail(2,"Stunning Kashmir","Hotel Gulmarg House",6,30899);
        dpd[2]=new dpackagesdetail(3,"Kerela Retreat","Vinice Residency",5,14640);
        dpd[3]=new dpackagesdetail(4,"Magical Udaipur","Revas Lake View",7,10989);
        dpd[4]=new dpackagesdetail(5,"South India Retreat","Ananya Greens",6,24900); // FIXED ID
        dpd[5]=new dpackagesdetail(6,"Uttrakhand","DLS Resort",4,24500); // FIXED ID

        dp.dpackage(dpd);
    }
}

class dpackagesdetail
{
    int tour_id;
    String tour_name;
    String stayin;
    int duration;
    double price;

    dpackagesdetail(int tour_id,String tour_name,String stayin,int duration,double price)
    {
        this.tour_id=tour_id;
        this.tour_name=tour_name;
        this.stayin=stayin;
        this.duration=duration;
        this.price=price;
    }
}

class dpackages
{
    void dpackage(dpackagesdetail dpd[])
    {
        displayall(dpd);
    }

    void displayall(dpackagesdetail[] dpd)
    {
        System.out.println("=========================================================================================");
        System.out.printf("| %-3s | %-35s | %-25s | %-7s | %-12s |\n",
        "ID", "Tour Name", "Stay-In Hotels", "Nights", "Price (Rs)");
        System.out.println("=========================================================================================");

        for (int i = 0; i < dpd.length; i++)
        {
            System.out.printf("| %-3d | %-35s | %-25s | %-7d | %-12.2f |\n",
            dpd[i].tour_id, dpd[i].tour_name, dpd[i].stayin, dpd[i].duration, dpd[i].price);
        }

        System.out.println("=========================================================================================");
    }
}

// FIXED missing class
class InternationalMenu {
    void options() {
        System.out.println("\nInternational Packages Coming Soon...\n");
    }
}

class buypackagedom extends MainPackagesdomestic
{
    Scanner sc = new Scanner(System.in);
    int dpchoice;
    int persons;
    String[][] travelers;

    buypackagedom()
    {
        System.out.print("Enter Tour Id (1-6): ");
        dpchoice = sc.nextInt();
        sc.nextLine();

        billingdom();
        generateBill();
    }

    void billingdom()
    {
        System.out.println("\nTraveller Details");
        System.out.print("How Many Persons Are Joining? ");

        persons = sc.nextInt();
        sc.nextLine();

        travelers = new String[persons][4];

        for (int i = 0; i < persons; i++)
        {
            System.out.println("\nTraveller " + (i + 1));
            System.out.print("First Name: ");
            travelers[i][0] = sc.nextLine();
            System.out.print("Last Name: ");
            travelers[i][1] = sc.nextLine();
            System.out.print("Date of Birth (DD/MM/YYYY): ");
            travelers[i][2] = sc.nextLine();
            System.out.print("Gender (M/F/O): ");
            travelers[i][3] = sc.nextLine();
        }
    }

    void generateBill()
    {
        dpackagesdetail selectedPackage = null;

        for (dpackagesdetail pkg : dpd)
        {
            if (pkg.tour_id == dpchoice)
            {
                selectedPackage = pkg;
                break;
            }
        }

        if (selectedPackage == null)
        {
            System.out.println("Invalid Tour ID. Please try again.");
            return;
        }

        double totalPrice = selectedPackage.price * persons;

        System.out.println("\n================= BILL =================");
        System.out.println("Tour Package: " + selectedPackage.tour_name);
        System.out.println("Stay-In Hotel: " + selectedPackage.stayin);
        System.out.println("Duration: " + selectedPackage.duration + " nights");
        System.out.println("Price Per Person: Rs " + selectedPackage.price);
        System.out.println("----------------------------------------");

        System.out.println("Travellers:");
        for (int i = 0; i < persons; i++)
        {
            System.out.println(" - " + travelers[i][0] + " " + travelers[i][1] +
            " | DOB: " + travelers[i][2] +
            " | Gender: " + travelers[i][3]);
        }

        System.out.println("----------------------------------------");
        System.out.println("Total Price: Rs " + totalPrice);
        System.out.println("========================================\n");
    }
}
