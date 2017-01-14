# C-Projects
Some C++ projects that I have done
/*
 * Name: Alexander Tung
 * January 18, 2015
 * Description: This program will take in a desired purchase as well as the
 * price of the desired purchase and the exchange rate to pesos. Then it will
 * output the exchange rate to pesos and vice versa as well as the unit prices
 * in the original currency as well as the peso currency.
 */

#include <iostream>
#include <string>
#include <iomanip>

using namespace std;

int main()
{
	string desired_purchase, price, exchange_rate;

	cout << "Enter the desired purchase: ";
	getline(cin, desired_purchase);
	cout << "Enter the price: ";
	getline(cin, price);
	cout << "Enter the exchange rate (in pesos), ";
	getline(cin, exchange_rate);
	cout << endl;

	double number_desired_purchase = stod(desired_purchase.substr(0, desired_purchase.find(" ", 0)));

	double number_price = stod(price.substr(0, price.find(" ", 0)));
	string currency = price.substr(price.find(" ", 0) + 1, price.length() - price.find(" ", 0) + 1);

	double exchange_in_peso = stod(exchange_rate.substr(exchange_rate.find("=", 0) + 2, exchange_rate.length() - exchange_rate.find("=", 0) + 2));

	cout << "Currency exchange:" << endl;
	cout << currency + "-to-peso rate" << setw(8) << fixed << setprecision(2) << exchange_in_peso << endl;

	double opposite_currency = 1 / exchange_in_peso;
	cout << "peso-to-" + currency + " rate" << setw(8) << fixed << setprecision(2) << opposite_currency << endl;

	cout << "Unit prices:" << endl;
	double unit_price_currency = number_price / number_desired_purchase;
	double unit_price_peso = (number_price * exchange_in_peso) / number_desired_purchase;

	cout << "in " + currency << setw(8 + 10) << fixed << setprecision(2) << unit_price_currency << endl;
	cout << "in peso" << setw(8 + 10 + currency.length() - 4) << fixed << setprecision(2) << unit_price_peso;

	return 0;
}
