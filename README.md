#include<iostream>
#include<stack>
#include<string>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

using namespace std;

string InfixToPostfix(string expression);
int HasHigherPrecedence(char operator1, char operator2);
bool IsOperator(char C);
bool IsOperand(char C);
bool isOperator(char ch)
{
    if (ch=='+' || ch=='-' || ch=='*' || ch=='/')
        return true;
    else
        return false;
}


int performOperation(int op1, int op2, char op)
{
    int ans;
    switch(op){
    case '+':
        ans = op2 + op1;
        break;
    case '-':
        ans = op2 - op1;
        break;
    case '*':
        ans = op2 * op1;
        break;
    case '/':
        ans = op2 / op1;
        break;
    }
    return ans;
}
int main(){
string expression;
cout<<"Enter Infix Expression:\n";
getline(cin,expression);
string postfix=InfixToPosfix(expression);
cout<<"Postfix = "<<postfix<<"\n";
char exp[1000], buffer[15];
int i,op1, op2, len, j, x;
stack<int> s;
cout<<"Lets calculate the output! Give space between every operands n operators!";
cin>>exp;
len = strlen(exp);
j=0;
for(i=0; i<len;i++){
	if(exp[i]>='0' && exp[i]<='9'){
	buffer[j++] = exp[i];
	}
	else if(exp[i]==' '){
		if(j>0){
		buffer[j] = '\0';
		x = atoi(buffer);
		s.push(x);
		j=0;
	}
}
	
	else if(isOperator(exp[i])){
	op1 = s.top();
	s.pop();
	op2 = s.top();
	s.pop();
	s.push(performOperation(op1, op2, exp[i]));
	}
}
cout<<"jawabannya adalah "<<s.top();
