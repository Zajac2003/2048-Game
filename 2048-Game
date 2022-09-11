#include <iostream>
#include <cstdlib>
#include <time.h>
#include <windows.h>
#include <conio.h>


using namespace std;

int tablica[4][4]=
{

    {0,0,0,0},
    {0,0,0,0},
    {0,0,0,0},
    {0,0,0,0},

};
int Null[16];
int poprzednia[4][4];

void instrukcja(){
cout<<"W = ^"<<endl;
cout<<"S = v"<<endl;
cout<<"A = <"<<endl;
cout<<"D = >"<<endl;
cout<<"Q = Cofnij ruch"<<endl;
}
void Save_Table(){

    for(int i=0;i<4;i++)
    {
        for(int j=0;j<4;j++)
        {
            poprzednia[i][j]=tablica[i][j];
        }
    }

}
int Move_Possible_Check(){
int a;

    for(int i=0;i<4;i++)
    {

        for(int j=0;j<4;j++)
        {

            a=tablica[i][j];

            if(a==tablica[i+1][j] && j+1<=3) return 1;
            if(a==tablica[i-1][j] && i-1>=0) return 1;
            if(a==tablica[i][j+1] && j+1<=3) return 1;
            if(a==tablica[i][j-1] && j-1>=0) return 1;
            if(a==0) return 1;

        }

    }

return 0;
}
int Complete_Check(){

for(int i=0;i<4;i++)
{
    for(int j=0;j<4;j++)
    {
        if(tablica[i][j]==2048) return 1;
    }
}
return 0;
}
int Merge_Up(){

int test=0, wykonanie=0;

for(int j=0;j<4;j++)
{

    for(int i=0;i<3;i++)
    {

        if(tablica[i][j]==tablica[i+1][j] && tablica[i][j]!=0)
        {

            wykonanie=1;
            tablica[i][j]*=2;
            tablica[i+1][j]=0;
            test=1;

        }

    }

test=0;
}

return wykonanie;
}
int Slide_Up(){
int wykonanie=0;
for(int a=0;a<4;a++)
{
    for(int j=0;j<4;j++)
    {

        for(int i=1;i<4;i++)
        {
            if(tablica[i-1][j]==0&&tablica[i][j]!=0)
            {
                tablica[i-1][j]=tablica[i][j];
                tablica[i][j]=0;
                wykonanie=1;
            }

        }

    }
}
return wykonanie;
}
int Merge_Down(){

int test, wykonanie=0;

for(int j=3;j>=0;j--)
{
    test=0;

    for(int i=2;i>=0;i--)
    {
        if(tablica[i+1][j]==tablica[i][j]&&tablica[i+1][j]!=0)
        {
            tablica[i+1][j]*=2;
            tablica[i][j]=0;
            test=1;
            wykonanie=1;
        }

    }
}
return wykonanie;
}
int Slide_Down(){

int wykonanie=0;

for(int a=0;a<4;a++)
{
    for(int j=0;j<4;j++)
    {
        for(int i=3;i>0;i--)
        {
            if(tablica[i][j]==0&&tablica[i-1][j]!=0)
            {
                tablica[i][j]=tablica[i-1][j];
                tablica[i-1][j]=0;
                wykonanie=1;
            }
        }
    }
}
return wykonanie;
}
void Seek_For_Null(){
for(int i=0;i<16;i++)
{
    Null[i]=0;
}

for(int i=0, kratka=0;i<4;i++)
    {
        for(int j=0;j<4;j++)
        {
            if(tablica[i][j]==0)
            {
                Null[kratka]=i*10+j;
                kratka++;
            }

        }
    }
}
int Slide_Left(){
int wykonanie=0;
    for(int a=0;a<4;a++)
    {
        for(int i=0;i<4;i++)
        {
            for(int j=0;j<3;j++)
            {
                if(tablica[i][j]==0&&tablica[i][j+1]!=0)
                {
                    tablica[i][j]=tablica[i][j+1];
                    tablica[i][j+1]=0;
                    wykonanie=1;
                }
            }
        }
    }
return wykonanie;
}
int Merge_Left(){
int wykonanie=0;
    for(int i=0;i<4;i++)
    {

        for(int j=0;j<3;j++)
        {

            if(tablica[i][j]==tablica[i][j+1]&&tablica[i][j]!=0)
            {
                tablica[i][j]*=2;
                tablica[i][j+1]=0;
                wykonanie=1;
            }

        }

    }
return wykonanie;
}
int Slide_Right(){

int wykonanie=0;
    for(int a=0;a<4;a++)
    {
        for(int i=0;i<4;i++)
        {

            for(int j=3;j>=1;j--)
            {

                if(tablica[i][j]==0&&tablica[i][j-1]!=0)
                {
                    tablica[i][j]=tablica[i][j-1];
                    tablica[i][j-1]=0;
                    wykonanie=1;
                }

            }

        }
    }
return wykonanie;
}
int Merge_Right(){
int wykonanie=0;
for(int i=0;i<4;i++)
    {

        for(int j=3;j>=1;j--)
        {

            if(tablica[i][j]==tablica[i][j-1]&&tablica[i][j]!=0)
            {
                tablica[i][j]*=2;
                tablica[i][j-1]=0;
                wykonanie=1;
            }

        }

    }
return wykonanie;
}
int Undo_Move(){

    int test=0;

    for(int i=0;i<4;i++)
    {
        for(int j=0;j<4;j++)
        {
            if(poprzednia[i][j]!=0) test=1;
        }
    }
    if(!test) return 0;

    for(int i=0;i<4;i++)
    {
        for(int j=0;j<4;j++)
        {
            tablica[i][j]=poprzednia[i][j];
        }
    }

return 1;
}
int Move_Input_n_Execute(){

char ruch;
ruch=_getch();
int zwrot=0, check=0;

switch(ruch)
{

    case 'w':
    {
        Save_Table();

        check+=Slide_Up();
        check+=Merge_Up();

        if(check>0) zwrot=1;

        Slide_Up();


        return zwrot;
        break;
    }

    case 'a':
    {
        Save_Table();

        check+=Slide_Left();
        check+=Merge_Left();

        if(check>0) zwrot=1;
        Slide_Left();

        return zwrot;
        break;
    }

    case 's':
    {
        Save_Table();

        check+=Slide_Down();
        check+=Merge_Down();

        if(check>0) zwrot=1;

        Slide_Down();

        return zwrot;
        break;
    }

    case 'd':
    {
        Save_Table();

        check+=Slide_Right();
        check+=Merge_Right();

        if(check>0) zwrot=1;
        Slide_Right();

        return zwrot;
        break;
    }

    case 'q':
    {

        Undo_Move();

        return zwrot;
        break;
    }

}
return zwrot;
}
void Random_Adder(int MoveCounter){

srand(time(NULL));
int liczba=rand()%10;

if(liczba>=0&&liczba<8)
{
    liczba=2;
}

else liczba=4;
/////At this moment the number is randomized and ready to input
/////next is randomizing spot

Seek_For_Null();
srand(time(NULL));

int a=(rand() + tablica[3][3] + tablica[2][3] + MoveCounter/3)%16; //NULLE

for(int licznik=0;Null[a]==0;a++,licznik++)
{
    if(licznik>10) break;
    if(a>=15) a=-1;

}

if(Null[a]==0)
{
    tablica[Null[0]/10][Null[a]%10]=liczba;
    return;
}



tablica[Null[a]/10][Null[a]%10]=liczba;

}
void Print(){
for(int i=0;i<4;i++)
{
    for(int j=0;j<4;j++)
    {
        cout<<tablica[i][j]<<"   ";
    }
    cout<<endl;
}


}
int main()
{
        int test=0;


        Random_Adder(0);

        for(int MoveCounter=0;;MoveCounter++)
        {

        if(Complete_Check() && !test)
        {
            cout<<"Gratulacje! Wygrales."<<endl;
            test=1;
        }

        if(!Move_Possible_Check()) cout<<"Przegrales."<<endl;

        Print();
        if(Move_Input_n_Execute()) Random_Adder(MoveCounter);

        system("cls");

        }


    return 0;
}
