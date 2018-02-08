// Assignment : Project 1
// File : paceP1.cpp
// Author : \Zack Pace/ 
// Description : Reads in a word.txt file into an array. Using a variety of functions, this
// program will print 7 strings of the input file per line, find the smallest and largest
// string, find the adjacent strings with the least and greatest similarity, print the
// longest Ascending and Descending Sequence, and finally, sort the array into ABC order.
// Enjoy!

#include <iostream>
#include <fstream>
#include <iomanip>
#include "similarity.hpp"
#include <string>

using namespace std;

int const MAXSTRINGS = 1000;
int const PERLINE = 7;

int GetStrings (string S []);
void PrintStrings (string S [], int C);
void PrintShortest (string S [], int C);
void PrintLongest (string S [], int C);
void GreatestSimilarity (string S [], int C);
void LeastSimilarity (string S [], int C);
void AscendingSequence (string S [], int C);
void DescendingSequence (string S [], int C);
void Sort (string S [], int C);
void Swap (string & a, string & b);

int main ()
{
  // Read string into array called Taner with maxwords of 1000.
  string Taner [MAXSTRINGS];
  cout << setw(12) << left << "The Strings:" << endl;
  int count = GetStrings(Taner);
  PrintStrings (Taner, count);
  PrintShortest (Taner, count);
  PrintLongest (Taner, count);
  LeastSimilarity (Taner, count);
  GreatestSimilarity (Taner, count);
  AscendingSequence (Taner, count);
  DescendingSequence (Taner, count);
  Sort(Taner, count);
  return 0;
}
int GetStrings (string S[])
{
  int count = 0;
  ifstream input;
  // Opens strings.txt into input.
  input.open("strings.txt");
  for (int i = 0; i < MAXSTRINGS; i++){
    input >> S[i];
    // Once there are no strings to be read, it closes the input file.
      if (S[i] == " " || S[i] == "")
	{
	  input.close();
	  return count;
	}
      count++;
  }
  input.close();
  // returns the number of strings in the array.
  return count;
}
void PrintStrings (string S [], int C)
{
  // Iterates through the array and prints 7 strings per line.
  int count = 0;
  for (int i = 0; i < C; i++){
    if (count >= 7){
      cout << "\n";
      count = 0;
    }
    cout << setw (12) << S[i];
    count++;
  }
  cout << "\n" << endl;
}
void PrintLongest (string S [], int C)
{
  // Compares the length of the string[i] with the variable "longest".
  string longest = "";
  for (int i = 0; i < C; i++){
    if (S[i].length() > longest.length())
      longest = S[i];
  }  
  cout << "Longest String: " << longest << endl << endl;
}

void PrintShortest (string S [], int C)
{
  // Compares the length of the string[i] with the variable "longest".
  string longest = "";
  for (int i = 0; i < C; i++){
    if (S[i].length() > longest.length())
      longest = S[i];
  }
  // Uses the longest variable as the Max for the variable "shortest".
  string shortest = longest;
  for (int i = 0; i < C; i++){
    if (S[i].length() < shortest.length())
      shortest = S[i];
  }
  cout << "Shortest String: " << shortest << endl << endl;
  
}

void GreatestSimilarity (string S [], int C)
{
  float similar = 0; // Num of similarities.
  float temp = 0;
  int GS1 = 0; // First word.
  int GS2 = 0; // Second word.
  // Compares the first word to the second word.
  for (int i = 1; i < C; i++){
    // Compares the percentage of similar between GS1&2 to the other greatest percentage.
    temp = similarity (S[i], S[i+1]);
    if(temp > similar){
      similar = temp;
      GS1 = i;
      GS2 = i+1;
    }
  }
  cout << setw(12) << "Adjacent Strings with Greatest Similarity: ";
  cout << setprecision(1) << fixed << S[GS1]  << " " << S[GS2] << " (" << similar << "%)";
  cout << endl << endl;
}

void LeastSimilarity (string S [], int C)
{
  float similar = 100; // Num of similarities.
  float temp = 0;
  int LS1 = 0; // First word.
  int LS2 = 0; // Second word.
  // Compares the first word to the second word.
  for(int i = 0; i < C-1; i++){
    // Compares the percnetage of similar between LS1&2 to the other least percentage
    temp = similarity (S[i], S[i+1]);
    if (temp < similar){
      similar = temp;
      LS1 = i;
      LS2 = i+1;
    }
  }
  
  cout << setw(12) << "Adjacent Strings with Least Similarity: ";
  cout << setprecision(1) << fixed << S[LS1] << ' ' << S[LS2] << " (" << similar << "%)";
  cout << endl << endl;
  
}

void AscendingSequence (string S [], int C)
{
  int i = 0;
  int var = 0; // element that begins the longest ascending sequence.
  int len = 0; // current greatest number.
  int tempCount = 0; // counter of number's in ascending sequence.
  int count = 0;
  // adds one to tempCount when i is less than i+1.
  for (int i = 0; i < C-1; i++)
    {
      if (S[i] < S[i+1])
	{
	  tempCount++;
	}
    // When i is greater than i+1.
      else if (S[i] > S[i+1])
	{
	  if(tempCount > len){
      // Saves tempCount to len
	    len = tempCount;
	    var = i - len;
       
	  }
	  tempCount = 0;
	}
    }
  cout << len;
  cout << setw(12) << "Ascending Sequence: " << endl;
  PrintStrings(&S[var], len+1);
  cout <<  endl;
}
  
  

void DescendingSequence (string S [], int C)
{
  int i = 0;
  int var = 0; // index of first string
  int len = 0; // Number of strings in the sequence 
  int tempCount = 0; // index of last string
  int count = 0;
  while (i < C){
    if (S[i] > S[i+1])
	  tempCount++;
    else if (tempCount > len){
      len  = tempCount;
      tempCount = 0;
      var = i - len;
    }
    else
      tempCount = 0;
    i++;
  }
  cout << "Descending Sequence:" << endl;
  PrintStrings(&S[var], len+1);
  cout << endl;
}
  	
void Sort (string S [], int C)
{
  int count = 0;
  bool TF = true;
  // Boolean statement that compares i & i+1.
  // Returns true if i > i+1, otherwise false.
  while (TF){
    TF = false;
    for(int i = 0; i < C-1; i++){
      if(S[i] > S[i+1]){
	Swap(S[i], S[i+1]);
	TF = true;
      }
    }
  }
  // Sorts array out in ABC order.
  cout << setw(12) << "Sorted Strings: " << endl;
  PrintStrings (S,C);
}

void Swap (string & a, string & b)
{
  // Switches A with B using a temporary variable to save A's value.
  string temp;
  temp = a;
  a = b;
  b = temp;
}
