# Programa 6

Linguagem Utilizada: C++.

Programa que faz a leitura do nome, sexo e salário de pessoas e retorna a média do salário dos homens e das mulheres, e o valor total dos salários.

Programa Desenvolvido no DEV C++ IDE.

Código:

#include "iostream"
#include "cstdlib"
#include "math.h"
#include "string.h"
#include "conio.h"
#include "windows.h" 
#include <iomanip>
using namespace std;
struct dados
{
	string nome;
	double sal;
	string sexo;
	
};
struct dados cad[10];

void armazenar(int line, string nom, double sa, string sex)
{
	cad[line].nome = nom;
	cad[line].sal = sa;
	cad[line].sexo = sex;
}

void exibir(int line, double homem, double mulher, double total)
{
	for (int i=0; i<= line; i++)
	{
	  cout << "\n" << cad[i].nome << " - " << cad[i].sal << " - " << cad[i].sexo << endl;	
	}
	
	cout << "\n\n";
	cout << "\nMedia dos salários dos homens: " << homem << endl;
	cout << "\nMedia dos salários das mulheres: " << mulher << endl;
	cout << "\nMedia total dos salários: " << total << endl;
		
	system("pause");
}

int calcular_homem(int line)
{
	int cont_homem = 0, soma_homem = 0;
	int media_homem;
	
	for (int i=0; i <= line; i++)
	{
		if (cad[i].sexo == "Masculino")
		{
		  soma_homem += cad[i].sal;
		  cont_homem ++;	
		}
	}
    
    media_homem = soma_homem/cont_homem;
    return media_homem;
}

int calcular_mulher(int line)
{
	int cont_mulher = 0, soma_mulher = 0;
	int media_mulher;
	
	for (int i=0; i <= line; i++)
	{
		if (cad[i].sexo == "Feminino")
		{
		  soma_mulher += cad[i].sal;
		  cont_mulher ++;	
		}
	}
    
    media_mulher = soma_mulher/cont_mulher;
    return media_mulher;
}

int calcular_total(int line)
{
	int cont_total = 0, soma_total = 0;
	int media_total;
	
	for (int i=0; i <= line; i++)
	{
		  soma_total += cad[i].sal;
		  cont_total ++;	
	}
    
    media_total = soma_total/cont_total;
    return media_total;
}


int menu()
{
	int tecla;
    system("cls");
    cout << "\n***Tela Inicial***\n";
    cout << "\n1 - Ler";
    cout << "\n2 - Realizar Cálculos";
    cout << "\n3 - Exibir Resultado";
    cout << "\n4 - Sair \n" << endl;
    cin >> tecla; 
    return tecla;
}

void contmenu()
{
	int tecla = 0, linha = -1;
	double sala = 0;
	int cal = 0;
	double med_hom = 0, med_mul = 0, med_tot = 0;
	string name;
	string se;
	while (tecla != 4)
	{
	  int teste = -1;
	  int condi = 0;
	  tecla = menu();
	
	   switch(tecla)
	   {
		case 1:
			{
				system("cls");
				
				cout << "\nDigite o nome: ";
				cin >> name;
				
				cout << "\nDigite o salário: ";
				cin >> sala;
				
				while(condi == 0)
				  {
				  cout << "\nDigite: [1] Masculino/[2] Feminino \n";
				  cin >> teste;
				  
				  if (teste == 1)
				  {
				  	se = "Masculino";
				  	condi = 1;
				  }
				  else if(teste == 2)
				  {
				  	se = "Feminino";
				  	condi = 1;
				  }
				  system("cls");
			      }
			      
				linha++;
				armazenar(linha, name, sala, se);
			    break;	
			}
		case 2:
			{
				if (linha >= 0)
				{
				   system("cls");
				   
				   med_hom = calcular_homem(linha);				   
				   med_mul = calcular_mulher(linha);
				   med_tot = calcular_total(linha);
				   
				   cout << "Calculando...";
				   Sleep(2000);
				   cal = 1;
				}
				break;
			}
		case 3:
			{
			  if (cal == 1)
			  {
				if (linha >= 0)
				{
					exibir(linha, med_hom, med_mul, med_tot);
				}
		      }
				break;
			}
	   }  
    }
}


int main()
{
	setlocale (LC_ALL, "portuguese");
	contmenu();
	
return 0;}
