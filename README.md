#include <iostream>
#include <iomanip>
#include <ctime>
#include <stdlib.h>
#include <memory>
#include <clocale>
using namespace std;
int main()
{
	setlocale(LC_ALL, "Russian");
	srand(time(NULL));
	int i, j, n, max, m, ifirst = 0, jfirst = 0, k = 0, imax = 0;
	cout << "Введите размер массива" << endl;
	cin >> n;
	cout << "\n" << "Заданная матрица размером " << n << "*" << n << " со случайными числами \n" << endl;
	double** a = new double* [n];
	for (i = 0; i < n; i++)
	{
		a[i] = new double[n];
	}
	for (i = 0; i < n; i++)
	{
		for (j = 0; j < n; j++)
		{
			a[i][j] = rand() % 200 - 100;
			cout << setw(5) << a[i][j] << " ";
		}
		cout << endl;
	}
	cout << endl;

	for (i = 0; i < n; i++)
	{
		for (j = 0; j < n; j++)
			if (a[i][j] < 0) { ifirst = i, jfirst = j; k++; break; }
		if (k == 1) break;
	}

	for (i = 0; i < n; i++)
		for (j = 0; j < n; j++)
			if (a[i][j] < 0 && ((i == ifirst && j == jfirst) || a[i][j] > max)) { max = a[i][j]; imax = i; }

	swap(a[0], a[imax]);

	for (i = 0; i < n; i++)
	{
		for (j = 0; j < n; j++)
			cout << setw(5) << a[i][j] << " ";
		cout << endl;
	}
	cout << endl;
	for (i = 0; i < n; i++)
		delete[] a[i];
	delete[] a;
	system("pause");
	return 0;
}
