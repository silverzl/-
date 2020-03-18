#include<stdio.h>
#include<string.h>
#include <ctype.h>
#include"malloc.h"

#define start 1
#define accepted_letter 2 
#define accepted_num 3
#define accepted_sign 4

int main(){
	
	int i=0;
	char *string=NULL;
	string=(char*)malloc(100*sizeof(char));
	memset(string, '\0', sizeof(string));
	
	int current_state=start;
	char current_char=getchar();
	while(current_char!=EOF){
		switch(current_state){
			case start:
				if(isalpha(current_char)) {	  //当第字母的时候 
				current_state=accepted_letter;				
				string[i]=current_char;
				i++;
			}else if(isdigit(current_char)){	//当为数字的时候 
				current_state=accepted_num;				
				string[i]=current_char;
				i++;
			}else if(ispunct(current_char)){	//当为符号时 
				current_state=accepted_sign;				
				string[i]=current_char;
				i++;
			}				
			break;
				
			case accepted_letter:			//接受字母循环   字母中标识符可能含有数字和下划线 不留字母口 
				if(!(isalnum(current_char)||current_char=='_')){
				current_state=start;
				puts(string);
				memset(string, 0, sizeof(string));
				i=0;
					if(ispunct(current_char)){	//在字母中留符号入口 
						current_state=accepted_sign;				
						string[i]=current_char;
						i++;
					} 
				break;
			}else{													
				string[i]=current_char;	
				i++;
				break;
			}
			
			case accepted_num:				//接受数字循环  //标识符不能以数字开头 
				if(!isdigit(current_char)){
				current_state=start;
				puts(string);
				memset(string, 0, sizeof(string));
				i=0;
					if(isalpha(current_char)){		//在数字中留字母口 
						current_state=accepted_letter;				
						string[i]=current_char;
						i++;
					}else if(ispunct(current_char)){	//在字母中留符号入口 
						current_state=accepted_sign;				
						string[i]=current_char;
						i++;
					}  
				break;
			}else{													
				string[i]=current_char;	
				i++;
				break;
			}
			
			case accepted_sign:			//接受特殊符号循环 
				if(!ispunct(current_char)){
				current_state=start;
				puts(string);
				memset(string, 0, sizeof(string));
				i=0;
					if(isdigit(current_char)){		//在符号中留数字口 
						current_state=accepted_num;				
						string[i]=current_char;
						i++;
					}else if(isalpha(current_char)){		//在符号中留字母口 
						current_state=accepted_letter;				
						string[i]=current_char;
						i++;
					}  
				break;
			}else{
				if(current_char=='('||current_char==')'||current_char=='{'||current_char=='}'){		//括号不能连续输出 
					current_state=start;
					puts(string);
					memset(string, 0, sizeof(string));
					i=0;
						if(ispunct(current_char)){	//仍需要留符号入口 
							current_state=accepted_sign;				
							string[i]=current_char;
							i++;
						}
					break;
				} 
								
				else{																
				string[i]=current_char;	
				i++;
				break;
			}
			}
			
			default:
				printf("error");
		}
		current_char=getchar();
	}
}
