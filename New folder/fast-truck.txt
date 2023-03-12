/* Fast Track Car Service Management System */
#include<stdio.h>
#include<conio.h>
#include<windows.h>
#include<string.h>
#include<stdlib.h>
#define MAX_SIZE 8
void login();//login screen function call
void welcomescreen();// Welcome Screen function call
void ChooseService();//Choose Service function call
void Add_rec();//Function Call used to add new records
void List_rec();// function call of list 
void show_rec();// function call to show saved records
void Title();
FILE *fptr;// used to create new file in a drive
int Service;
int i,num,sum=0;
int arr[MAX_SIZE];
/*
void main()
{
	int a=1;
	while(a==1)
	{
		ChooseService();
	}
}
*/
struct customer
{
char Customer_Name[30];
char Service_Date[30];
char Registration_Number[20];
char Service_Needed[20];
char Typeof_Service[20];
char Service_Fee[20];
};
struct customer p, temp_c;
int main()
{
	login();
	return 0;
}
void login()//login function
{
char password[10],username[10],ch;
printf("\n\n\t\t\t\t           FAST TRACK CAR SERVICE MANAGEMENT SYSTEM");
printf("\n________________________________________________________________________________________________________________________");
printf("\n\n\t\t ENTER USERNAME AND PASSWORD: ");
printf("\n\n\t\t USERNAME :: ");
scanf("%s",username);
printf("\n\t\t PASSWORD :: ");
scanf("%s",password);
if(strcmp(username,"ADMIN")==0&&strcmp(password,"Password")==0)//function to compare the user id and password
{
	printf("LOGIN SUCCESSFULL");
	system("cls");// used to clear screen
	WelcomeScreen();
}
else
{
	printf("INCORRECT PASSWORD");
}
getch();
system("cls");
login();
}
void WelcomeScreen()//WelcomeScreen Call
{
  printf("\n\t\t\t\t\t\t\t# WELCOME TO #");
  printf("\n\t\t\t\t\t  FAST TRACK CAR SERVICE MANAGEMENT SYSTEM");
  printf("\n________________________________________________________________________________________________________________________\n");
	int a;
	printf("\n\n\t\t\t\t1. Add Customers Record\n");
	printf("\n\t\t\t\t2. List Customers Record\n");
	printf("\n\t\t\t\t3. LogOut\n");
	printf("\n\n\t\t\t\t Choose from 1 to 3: ");
    scanf("%i", &a);
    
    switch(a)
    {
    	case 1:
    		system("cls");
    		Add_rec();
			break;
		case 2:
			system("cls");
			show_rec();
			break;
		case 3:
			system("cls");
			login();
			break;  		
	}	
		  
}
void Add_rec()
{
	fptr = fopen("fast-track_Accounts.txt","w");//creating a file name fast-track accounts in D: drive
	if(fptr==NULL)
	{
		printf("File Does not exists \n");
		return;
	}
	printf("\nEnter Customer Name: ");
	scanf("%s",&p.Customer_Name);
	fprintf(fptr,"Customer_Name:: %d\n",p.Customer_Name);
	printf("\nEnter Service Date: ");
	scanf("%s",&p.Service_Date);
	fprintf(fptr,"Service_Date:: %d\n",p.Service_Date);
	printf("\nEnter Registration Number: ");
	scanf("%s",&p.Registration_Number);
	fprintf(fptr,"Registration Number:: %d\n",p.Registration_Number);
	printf("\n\n\nAccount Created..\n");
	printf("________________________________________________________________________________________________________________________\n");
	fclose(fptr);
	getch();
	system("cls");
	List_rec();
}
void List_rec()
{   fptr = fopen("fast-track_Accounts.txt","w");
	if(fptr==NULL)
	{
		printf("File Does not exists \n");
		return;
	}
     printf("\n\t\tChoose from the below table:-");
	 printf("\n________________________________________________________________________________________________________________________");
	 printf("\n\n\n\tNo\tService type\t\t\t\t Time Needed(min)\t Service Fee ( Normal / Urgent)");
	 printf("\n\t1.\tRepair punctured car tyre / piece       10 Min.                    (10RM / 12RM) ");
     printf("\n\t2.\tMineral Oil Change                      15 Min.                    (150RM / 160RM)");
	 printf("\n\t3.\tCar tyre change / piece                 20 Min.                    (80RM / 90RM)");
	 printf("\n\t4.\tSynthetic Oil Change                    20 Min.                    (130RM / 140RM)");
	 printf("\n\t5.\tBattery Change                          5 Min.                     (200RM / 210RM)");
	 printf("\n\t6.\tHead Light Bulb change / piece          5 Min.                     (6RM / 8RM)");
	 printf("\n\t7.\tTail Light bulb change / piece          5 Min.                     (8RM / 6RM)");
	 printf("\n\t8.\tCar Wash                                10 Min.                    (10RM / 12RM)");  
	  
	 printf("\n\n\nHow many Services from above do you want (should be one number): ");
	 scanf("%d",&num);
	 fprintf(fptr,"Number of services:: %d\n",num);
	 printf("\nWhich Number of Service (enter service number):\n");
	 for (i=0; i<num; i++)
	 scanf("%s",p.Service_Needed);
	 fprintf(fptr,"Service_Needed:: %d\n",p.Service_Needed);
	 printf("\nEnter Type of Service which you want (Normal/Urgent): ");
	 scanf("\n%s",&p.Typeof_Service);
	 fprintf(fptr,"Typeof_Service:: %d\n",p.Typeof_Service);
	 printf("\nEnter Service Fee:\n ");
	 for (i=0; i<num; i++)
     {  
	  scanf("\n%d",&arr[i]);
	  sum += arr[i];
     }
     printf("\nTotal service fee = %d", sum);
     fprintf(fptr,"Total service fee:: %d\n",sum);
     /* fprintf(ptr,"%s,%s,%s,%s,%s,%s",p.Customer_Name,p.Service_Date,p.Registration_Number,p.Service_Needed,p.Typeof_Service,p.Service_Fee ); */
     printf("\n.............................................Information Record Sucessfully.............................................");
     fclose(fptr);
	 getch();
}
void show_rec()//shows the saved records
{
	printf("\nCustomer Name:: %s",p.Customer_Name);
	printf("\nService Date:: %s",p.Service_Date);
	printf("\nRegistration Number:: %d",p.Registration_Number);
	printf("\nNumber of Service:: %d",num);
	printf("\nType of Service:: %d ",p.Service_Needed);
	printf("\nservice fee = %d", sum);
}

