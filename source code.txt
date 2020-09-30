#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <conio.h>
char wct[]="\n\t\t\t\t\t\t\tGROCERIES STORE",line[]="\n________________________________________________________________________________________________________________________";
char id[20],pass[20];
int d=1,p=1,b1=0,qty,i;
float total=0;

struct cart
{
    int pcode;
    char pnm[100];
    int pqty;
    float pprice;
}c1[20];
struct cart c[16]={{100,"Milk(1L)",50,55},
                   {101,"Curd(200g)",50,30},
                   {102,"Cottage cheese(200g)",50,40},
                   {103,"Cheese(200g)",50,80},
                   {104,"Soap(150g)",50,20},
                   {105,"Shampoo(1L)",50,99},
                   {106,"Face Wash(300ml)",50,59},
                   {107,"Cold Drink(1.2L)",50,60},
                   {108,"Fruit juice(1L)",50,89},
                   {109,"McCain Smiles(200g)",50,69},
                   {110,"Deodorant(500mL) ",50,250},
                   {111,"Sanitary Napkin",50,50},
                   {112,"Hair Gel(300mL)",50,95},
                   {113,"Hair oil(300mL)",50,120},
                   {114,"Shaving cream(100g)",50,25},
                   {115,"Shaving Blade(10 nos.)",50,59}
                  };

void login(void)
{
    int attempt=5;
    RE:
        printf("\nID: ");
        scanf("%s",id);
        printf("\nPassword: ");
        scanf("%s",pass);
        d=strcmp(id,"19125");
        p=strcmp(pass,"nuv");
        attempt--;
        if(attempt==0)
        {
            printf("\nToo many attempts exit program.!");
            getch();
            exit(0);
        }

        if(d!=0||p!=0)
        {
            printf("\nWrong id or password!Try Again!\nTries left %d.",attempt);
            goto RE;
        }

}
int product(void)
{int adch,ch;
   a0:
        printf("\n1.Dairy Products\n2.Bathing essentials\n3.Refrigerated items\n4.Hygiene\n5.Grooming\nEnter choice(1-7): ");
                scanf("%d",&adch);
                switch(adch)
                {case 1:a1: printf("\n1.Milk(1L)\n2.Curd(200g)\n3.Cottage cheese(200g)\n4.Cheese(200g)\n Enter choice(1-5):");
                        scanf("%d",&ch);
                        switch(ch)
                        {
                            case 1:return(c[0].pcode);break;
                            case 2:return(c[1].pcode);break;
                            case 3:return(c[2].pcode);break;
                            case 4:return(c[3].pcode);break;
                            default:printf("Invalid choice!enter again:");goto a1;break;
                        }break;
                 case 2:a2: printf("\n1.Soap(150g)\n2.Shampoo(1L)\n3.Face Wash(300mL)\n Enter Choice(1-3): ");
                            scanf("%d",&ch);
                            switch(ch)
                        {
                            case 1:return(c[4].pcode);break;
                            case 2:return(c[5].pcode);break;
                            case 3:return(c[6].pcode);break;
                            default:printf("Invalid choice!enter again:");goto a2;break;
                        }break;
                 case 3: a3: printf("\n1.Cold drink(1.2L)\n2.Fruit juice(1L)\n3. McCain smiles(200g)\n Enter Choice(1-3): ");
                             scanf("%d",&ch);
                            switch(ch)
                        {
                            case 1:return(c[7].pcode);break;
                            case 2:return(c[8].pcode);break;
                            case 3:return(c[9].pcode);break;
                            default:printf("Invalid choice!enter again:");goto a3;break;
                        }break;
                 case 4: a4: printf("\n1.Deodorant(500mL)\n2.sanitary napkin\n3.Hair Gel(200mL)\n4.Hair oil(300mL)");
                             printf("\n5.Shaving cream(100g)\n6.Shaving Blade(10 nos.)\n Enter Choice(1-6): ");
                             scanf("%d",&ch);
                            switch(ch)
                        {
                            case 1:return(c[10].pcode);break;
                            case 2:return(c[11].pcode);break;
                            case 3:return(c[12].pcode);break;
                            case 4:return(c[13].pcode);break;
                            case 5:return(c[14].pcode);break;
                            case 6:return(c[15].pcode);break;
                            default:printf("Invalid choice!enter again:");goto a4;break;
                        }break;
                default:printf("Invalid choice!enter again:");goto a0;
                        break;


                }
}

void pay(void)
{
    int pm,ch;
    if(total>1000)
    {
        printf("\nTotal discount 10percent because bill exceeding Rs 1000");
        total=total-(total*0.1);
    }
   a9:  printf("\nFinal amount to Pay:%f \nSelect Payment Method\n1.Card\n2.Cash \nEnter Choice:",total);
    scanf("%d",&pm);
    switch(pm)
    {
        case 1:a8: printf("\nSelect Card \n1.SBI Debit/Credit card \n2.Axis Debit/Credit card \n3.ICICI Debit/Credit card\nEnter choice: ");
                scanf("%d",&ch);
                switch(ch)
                {
                    case 1: printf("Amount: Rs %f paid\n Thank you!",total);printf("\nPress any key to go to main menu!");
                            getch();break;
                    case 2: printf("Amount: Rs %f paid\n Thank you!",total);printf("\nPress any key to go to main menu!");
                            getch();break;
                    case 3: printf("Amount: Rs %f paid\n Thank you!",total);printf("\nPress any key to go to main menu!");
                            getch();break;
                    default: printf("\nInvalid choice!Enter Again!");goto a8;
                }
        case 2: printf("Amount: Rs %f paid in cash \n Thank you!",total);break;
        default : printf("\nInvalid choice!Enter Again!");goto a9;
    }
}

void cartt(void)
{
    char yn[3];
    system("cls");puts(line);puts(wct);puts(line);
    printf("\nCART:\n");
    bill();
    printf("\nTotal amount: %f",total);
    a7:
    printf("\nBUY?(Y/N): ");
    scanf("%s",yn);
    if(strcmpi(yn,"Y")==0)
    {
     pay();
    }
    else if(strcmpi(yn,"N")==0)
    {
        printf("press any key to go to Main menu.");
        getch();
    }
    else
        {
            printf("\nInvalid Choice!");
            goto a7;
        }

}
void bill(void)
{
    for(i=0;i<b1;i++)
    {
        printf("%d.%s price:%1.1f Quantity:%d\n",c1[i].pcode,c1[i].pnm,c1[i].pprice,c1[i].pqty);
        total+=c1[i].pprice*c1[i].pqty;
    }
}
void buy(void)
{
    int by,ch;
    char yn[3];
    system("cls");puts(line);puts(wct);puts(line);
    b:
    by=product();
    by-=100;
    printf("\n%d.%s \nprice:%f",c[by].pcode,c[by].pnm,c[by].pprice);
    printf("\nQuantity of %s: ",c[by].pnm);
    scanf("%d",&qty);
    printf("\nAdd to cart(Y/N)?");
    scanf("%s",yn);
    if(strcmpi(yn,"Y")==0)
    {
        c1[b1]=c[by];
        c1[b1].pqty=qty;
        c[by].pqty-=qty;
        printf("\nAdded to cart!");
        b1++;
    }
    else if(strcmpi(yn,"N")==0)
    {
        goto a6;
    }
    else
    {
       printf("\ninvalid choice!!");
       goto b;
    }
       a6:
        printf("\n1.Add more products to cart?\n2.Goto cart?");
        scanf("%d",&ch);
        if(ch==1)
        {
            goto b;
        }
        else if (ch==2)
        {
           cartt();
        }
        else
        {
            printf("\nInvalid Choice!");
            goto a6;
        }


}

void manage(void)
{
    int choice,code,qty;
    system("cls");puts(line);puts(wct);puts(line);
    printf("\n\t\t\t\t\t\t|\tCHOOSE          |");
    printf("\n\t\t\t\t\t\t|***********************|");
    printf("\n\t\t\t\t\t\t|\t1.ADD ITEM      |");
    printf("\n\t\t\t\t\t\t|\t2.DELETE ITEM   |");
    printf("\n\t\t\t\t\t\t|\t3.CHECK STOCK   |");
    printf("\n\t\t\t\t\t\t|***********************|");
    printf("\n\t\t\t\t\t\t \tEnter choice(1-3): ");
    scanf("%d",&choice);
    switch(choice)
    {
        case 1: printf("\nSelect to add:");
                code=product();
                code-=100;
                printf("\n Amount to add %s",c[code].pnm);
                scanf("%d",&qty);
                c[code].pqty+=qty;
                printf("\nAdded!");
                break;
        case 2: printf("\nSelect what to delete");
                code=product();
                code-=100;
                printf("\n Amount to add %s",c[code].pnm);
                scanf("%d",&qty);
                c[code].pqty+=qty;
                printf("\nAdded!");
                break;
        case 3: for(i=0;i<16;i++)
                {
                    printf("%d.%s price:%1.1f Quantity:%d\n",c1[i].pcode,c1[i].pnm,c1[i].pprice,c1[i].pqty);
                }
                break;

    }
}

int main()
{
    int choice;
    a:
    system("cls");
    puts(line);
    puts(wct);
    puts(line);
    printf("\n\t\t\t\t\t\t|\tMAIN MENU       |");
    printf("\n\t\t\t\t\t\t|***********************|");
    printf("\n\t\t\t\t\t\t|\t1.LOGIN         |");
    printf("\n\t\t\t\t\t\t|\t2.MANAGE        |");
    printf("\n\t\t\t\t\t\t|\t3.BUY           |");
    printf("\n\t\t\t\t\t\t|\t4.CHECK BILL    |");
    printf("\n\t\t\t\t\t\t|\t5.EXIT          |");
    printf("\n\t\t\t\t\t\t|***********************|");
    printf("\n\t\t\t\t\t\t \tEnter choice: ");
    scanf("%d",&choice);
    switch(choice)
    {
        case 1: system("cls");puts(line);puts(wct);puts(line);
                login();
                goto a;
        case 2: system("cls");puts(line);puts(wct);puts(line);
                if(d!=0&&p!=0)
                {
                    printf("\nAuthenticate Yourself! ");
                    login();
                }
                manage();
                goto a;
        case 3: system("cls");puts(line);puts(wct);puts(line);
                if(d!=0&&p!=0)
                {
                    printf("\nAuthenticate Yourself! ");
                    login();
                }
                buy();
                goto a;
        case 4:system("cls");puts(line);puts(wct);puts(line);
                if(d!=0&&p!=0)
                {
                    printf("\nAuthenticate Yourself! ");
                    login();
                }
                bill();
                goto a;
        case 5:exit(0);
        default: printf("\nInvalid choice!!enter again!!");getch();goto a;

    }
 return 0;
}
