#include <iostream>
#include <string>
using namespace std;
int main()
{
	int x, y; double result;
	cout << " Enter 2 int number : ";
	cin >> x >> y;
	try
	{
		if (y == 0) throw "Error";
		result = static_cast <double> (x) / y;
		cout << "x / y = " << result << endl;
	}
	catch (const char* s)
	{
		cout << s << ": Division by zero" << endl;
	}
}
