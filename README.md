# t52
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#define COL 5
#define LIN 5


typedef struct
{
	char matriz[LIN][COL];
}controle;

char gera_caracter();
int gera_posicao();

void popula_matriz(controle *game)
{
	int r_line, r_col;
	do
	{
		r_line = gera_posicao();
		r_col = gera_posicao();
	}while(game->matriz[r_line][r_col] != '0');
	game->matriz[r_line][r_col] = gera_caracter();
}
void inicializa_matriz(controle *game)
{
	int r_line, r_col;
	r_line = gera_posicao();
	r_col = gera_posicao();
	for(int i = 0; i < LIN; i++)
	{
		for(int j = 0; j < COL; j++)
		{
			game->matriz[i][j] = '0';
		}
	}
	popula_matriz(game);	
}

void imprime_matriz(controle *game)
{
	for(int i = 0; i < LIN; i++)
	{
		for(int j = 0; j < COL; j++)
		{
			printf("|%c|", game->matriz[i][j]);
		}
		printf("\n");
	}	
}
int gera_posicao()
{
	int pos;
	pos = rand() % 5;
	return pos;
}

char gera_caracter()
{
	int letra;
	letra = rand() % 4;
	if(letra == 3)
	{
		return 'B';
	}
	else
	{
		return 'A';
	}
}
int main()
{
	controle game;
	srand(time(NULL));
	inicializa_matriz(&game);
	imprime_matriz(&game);
	popula_matriz(&game);
	imprime_matriz(&game);

}
