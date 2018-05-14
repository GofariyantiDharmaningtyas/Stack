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
