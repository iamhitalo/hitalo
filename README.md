#include <stdio.h>
#include <stdlib.h>
#include <locale.h>

int main ( ){
	int i, j, linha, coluna, contador;
	char matriz[3][3];
	
	setlocale(LC_ALL,""); /*Acentuação*/
	
	
	for(i = 0; i < 3; i++){
		putchar('\n');
		for(j = 0; j < 3; j++){
			putchar('\t');
			matriz[i][j] = '.';
			printf("%c", matriz[i][j]);
		}
		putchar('\n');
		putchar('\n');
	}
	//primeiro jogador sempre será 'x' e o segundo sempre será 'O';
	for (contador = 0; contador < 9; contador++){
		
		printf("\nInsira a linha em que deverá ser posto seu símbolo:\n");
		scanf("%d", &linha);
		fflush(stdout);
		linha--;
		
		printf("Insira a coluna em que deverá ser posto seu símbolo:\n");
		scanf("%d", &coluna);
		fflush(stdout);
		coluna--;
		
		putchar('\n');
		if(matriz[linha][coluna] == '.'){
		
			if(contador%2){
				matriz[linha][coluna] = 'O';
			} 
			else{
				matriz[linha][coluna] = 'X';
			}
			for(i = 0; i < 3; i++){
				putchar('\n');
				for(j = 0; j < 3; j++){
					putchar('\t');
					printf("%c", matriz[i][j]);
				}
				putchar('\n');
				putchar('\n');
			}
			if((matriz[0][0] == matriz[0][1] && matriz[0][0] == matriz[0][2] && matriz[0][0] != '.')||
			   (matriz[0][0] == matriz[1][1] && matriz[0][0] == matriz[2][2] && matriz[0][0] != '.')||
			   (matriz[0][0] == matriz[1][0] && matriz[0][0] == matriz[2][0] && matriz[0][0] != '.')||
			   (matriz[0][1] == matriz[1][1] && matriz[0][1] == matriz[2][1] && matriz[0][1] != '.')||
			   (matriz[0][2] == matriz[1][2] && matriz[0][2] == matriz[2][2] && matriz[0][2] != '.')||
			   (matriz[1][0] == matriz[1][1] && matriz[1][0] == matriz[1][2] && matriz[1][0] != '.')||
			   (matriz[2][0] == matriz[2][1] && matriz[2][0] == matriz[2][2] && matriz[2][0] != '.')||
			   (matriz[2][0] == matriz[1][1] && matriz[2][0] == matriz[0][2] && matriz[2][0] != '.')){
					
				printf("\nQue daora! O jogador %d ganhou! VAASSSSCOOO!", (contador%2) + 1);	
			}
		}
		else{
			printf("\nEsse espaço já está preenchido, cara! Que tal tentar outro? ;) \n");
			contador--;
		}
	}
	
	printf("\nF no chat, deu velha... ");
	exit(0);
}
