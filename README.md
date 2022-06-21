კურსის დასახელება : ობიექტზე ორიენტირებული დაპროგრამება 1 (C++)       კურსის  სტატუსი : ძირითადი
ქულების განაწილება : 1 –  8 ქულა, 2 – 14 ქულა, 3 – 9 ქულა, 4 – 4 ქულა, 5 – 5 ქულა
ქულების ჯამი : 40 ქულა
გამოცდის ხანგრძლივობა : 3  საათი

1.	შექმენით კლასები Fridge(მაცივარი) და Bookcase(წიგნების კარადა).ყოველ კლასში შემოიღეთ : დავალების პირობის შესაბამისი private მონაცემები; უპარამეტრო კონსტრუქტორი, რომელიც ობიექტის შექმნისთანავე უზრუნველყოფს მისი მონაცემების შემოტანას კლავიატურიდან და, თუ საჭიროა, კლასის სხვა ფუნქციები.
ასევე დაწერეთ მაცივრის და კარადის სიმაღლეების შედარების ფუნქცია ისე, რომ  იგი იყოს Bookcase კლასის ფუნქცია, ხოლო Fridge კლასის – მეგობარი ფუნქცია.
ძირითად ფუნქციაში შექმენით ორივე კლასის თითო–თითო ობიექტი, გამოიძახეთ სიმაღლეების შედარების ფუნქცია და დაბეჭდეთ უმცირესი სიმაღლის მქონე ობიექტის მოცულობა.თუ სიმაღლეები ტოლია, დაბეჭდეთ მაცივრის სიგანე, ფერი და ფასი.

#include<iostream>
using namespace std;
class Fridge; // forward declaration
class Bookcase {
	// private data members
private:
	double height, length, width, price;
	string color;
	// access specifier
public:
	// default constructor
	Bookcase();
	// destructor
	~Bookcase();
	// member function section
	bool compare(const Fridge&);
	double get_Capacity()const;
	double get_Height()const;
};
class Fridge {
	// private data members
private:
	double height, length, width, price;
	string color;
	// access specifier
public:
	// default constructor
	Fridge();
	// destructor
	~Fridge();
	// member function section
	friend bool Bookcase::compare(const Fridge&);
	double get_Capacity()const;
	void printINFO()const;
	double get_Height()const;
};
// -------------------- class (Fridge) declaration section --------------------
Fridge::Fridge() {
	cout << "Creating object of class Fridge..." << endl;
	cout << " -> Enter height : "; cin >> height;
	cout << " -> Enter length and width : "; cin >> length >> width;
	cout << " -> Enter color : "; cin >> color;
	cout << " -> Enter price : "; cin >> price; cout << endl;
}
double Fridge::get_Capacity()const { return (length * width * height); }
void Fridge::printINFO()const {
	cout << " -> Fridge's width is : " << width << endl
		<< " -> Fridge's color is : " << color << endl
		<< " -> Fridge's price is : " << price << endl << endl;
}
double Fridge::get_Height()const { return height; }
Fridge::~Fridge() = default;
// -------------------- class (Bookcase) declaration section --------------------
Bookcase::Bookcase() {
	cout << "Creating object of class Bookcase..." << endl;
	cout << " -> Enter height : "; cin >> height;
	cout << " -> Enter length and width : "; cin >> length >> width;
	cout << " -> Enter color : "; cin >> color;
	cout << " -> Enter price : "; cin >> price; cout << endl;
}
bool Bookcase::compare(const Fridge & F) {
	int result;
	if (height < F.height)
		result = 1;
	else if (height > F.height)
		result = 0;
	return result;
}
double Bookcase::get_Capacity()const { return (length * width * height); }
double Bookcase::get_Height()const { return height; }
Bookcase::~Bookcase() = default;

// -------------------- main function section --------------------
int main() {
	system("color A");
	Fridge myFridge;
	Bookcase myBookcase;

	if (myFridge.get_Height() == myBookcase.get_Height())
		myFridge.printINFO();
	else if (myBookcase.compare(myFridge))
		cout << " -> The capacity of an object with the smallest height is : " << myBookcase.get_Capacity() << endl;
	else
		cout << " -> The capacity of an object with the smallest height is : " << myFridge.get_Capacity() << endl;
}







2.	ააგეთ კლასების შემდეგი იერარქია :
ა).საბაზო Doctor(მეცნიერებათა დოქტორი) კლასის მონაცემებია firstName(სახელი), lastName(გვარი) და thesis(დისერტაციის დაცვის წელი);  კლასის ფუნქციებია – პარამეტრებიანი კონსტრუქტორი, დესტრუქტორი  და სხვა ფუნქციები საჭიროების მიხედვით;
ბ).მეორე საბაზო Researcher(მკვლევარი) კლასის მონაცემებია publications(პუბლიკაციების რაოდენობა) და projects(პროექტების რიცხვი);  კლასის ფუნქციებია – პარამეტრებიანი კონსტრუქტორი, დესტრუქტორი  და სხვა ფუნქციები საჭიროების მიხედვით;
გ).ორივე კლასის მემკვიდრე Lecturer(ლექტორი) კლასში დაამატეთ მონაცემები highSchool(უმაღლესი სკოლის დასახელება) და courses(ჩატარებული კურსების რიცხვი), შემოიღეთ პარამეტრებიანი კონსტრუქტორი, დესტრუქტორი  და სხვა ფუნქციები საჭიროების მიხედვით.კლასის ობიექტისთვის გადატვირთეთ >> და << ოპერატორები.ასევე გადატვირთეთ < ოპერატორი როგორც  Lecturer კლასის ფუნქცია.
	main - ში  შეასრულეთ შემდეგი დავალებები :
1)   შექმენით Doctor და Researcher კლასების თითო - თითო სტატიკური ობიექტი რაიმე კონკრეტული მნიშვნელობებით და შემდეგ დაბეჭდეთ ინფორმაცია მათ შესახებ;
2)   გააკეთეთ განაცხადი ლექტორების დინამიკურ მასივზე და შეავსეთ იგი მონაცემებით teachers.txt ფაილიდან.ლექტორების რაოდენობა არ აღემატება 800–ს.
სტანდარტული sort ალგორითმის და გადატვირთული < ოპერატორის გამოყენებით დაალაგეთ  ლექტორების მასივი პუბლიკაციების რაოდენობის კლებადობის მიხედვით.დალაგებული მასივი დაბეჭდეთ ეკრანზე.
	შემდეგ დაწერეთ კოდის ფრაგმენტი, რომელიც reference.txt ფაილში დაბეჭდავს იმ ლექტორების მონაცემებს, რომელთა პუბლიკაციების რიცხვი არის უმცირესი, უდიდესი, და  ყველაზე  ახლოს ყველა ლექტორის პუბლიკაციების საშუალო  რაოდენობასთან.
	ბოლოს, გაათავისუფლეთ დაკავებული დინამიკური მეხსიერება.


#include <iostream>
#include <fstream>
#include <algorithm>
	using namespace std;
// base class Doctor
class Doctor {
	// protected data members
protected:
	string firstName;
	string lastName;
	int thesis;
	// access specifier
public:
	// default constructor
	Doctor();
	// explicit value constructor
	Doctor(string, string, int);
	// destructor
	~Doctor();
	// member function section
	void printDoctror(ostream&)const;
};
// base class Researcher
class Researcher {
	// protected data members
protected:
	int publications;
	int projects;
	// access specifier
public:
	// default constructor
	Researcher();
	// explicit value constructor
	Researcher(int, int);
	// destructor
	~Researcher();
	// member function section
	void printResearcher(ostream&)const;
};
// derived class Lecturer (Doctor,Researcher)
class Lecturer : public Doctor, Researcher {
	// protected data members
protected:
	string highSchool;
	int courses;
	// access specifier
public:
	// default construcot
	Lecturer();
	// explicit value constructor
	Lecturer(string, string, int, int, int, string, int);
	// destructor
	~Lecturer();
	// member function section
	void printLecturer(ostream&)const;
	int get_Publications()const;
	// overloading function section
	friend istream& operator >> (istream&, Lecturer&);
	friend ostream& operator << (ostream&, const Lecturer&);
	bool operator < (const Lecturer&);
};
// -------------------- base class (Doctor) declaration section --------------------
Doctor::Doctor() {}
Doctor::Doctor(string f, string l, int t) : firstName(f), lastName(l), thesis(t) {}
void Doctor::printDoctror(ostream & out)const {
	out << " -> firstName - " << firstName << endl
		<< " -> lastName - " << lastName << endl
		<< " -> thesis - " << thesis << endl;
}
Doctor :: ~Doctor() = default;
// -------------------- base class (Researcer) declaration section --------------------
Researcher::Researcher() {}
Researcher::Researcher(int p, int pr) : publications(p), projects(pr) {}
void Researcher::printResearcher(ostream & out)const {
	out << " -> publications - " << publications << endl
		<< " -> projects - " << projects << endl;
}
Researcher :: ~Researcher() = default;
// -------------------- derived class (Lecturer) declaration section --------------------
Lecturer::Lecturer() {}
Lecturer::Lecturer(string f, string l, int t, int p, int pr, string h, int c) : Doctor(f, l, t), Researcher(p, pr), courses(c), highSchool(h) {}
Lecturer :: ~Lecturer() {}
istream& operator >>(istream & in, Lecturer & l)
{
	return in >> l.firstName >> l.lastName >> l.thesis >> l.publications >> l.projects >> l.highSchool >> l.courses;
}
void Lecturer::printLecturer(ostream & out)const
{
	printDoctror(out);
	printResearcher(out);
	out << " -> Highschool - " << highSchool << endl
		<< " -> courses - " << courses << endl;
}
ostream& operator <<(ostream & out, const Lecturer & l)
{
	l.printLecturer(out);
	return out;
}
bool Lecturer :: operator < (const Lecturer & l) {
	return this->publications > l.publications;
}
int Lecturer::get_Publications()const { return publications; }
// -------------------- global function --------------------
int FillArray(Lecturer * l)
{
	int counter = 0;
	ifstream ifs("teachers.txt");
	while (!ifs.eof())
	{
		ifs >> l[counter++];
	}
	return counter;
}
int getNearestIndex(Lecturer * l, int size) {
	int sum = 0, index = 0, average = 0;
	for (size_t i = 0; i < size; i++)
		sum += l[i].get_Publications();
	average = sum / size;
	for (size_t i = 0; i < size; i++)
	{
		if (l[i].get_Publications() > average)
			index = i;
		else break;
	}
	int first = abs(average - l[index].get_Publications());
	int second = abs(average - l[index + 1].get_Publications());
	if (first < second)
		return index;
	return (index + 1);
}
void LastTask(Lecturer * l, int size)
{
	ofstream ofs("reference.txt");
	ofs << "      Least " << endl;
	l[size - 1].printLecturer(ofs);
	ofs << "      Greatest " << endl;
	l[0].printLecturer(ofs);
	ofs << "   Closest to the average number of publications of all lecturers" << endl;
	int index = getNearestIndex(l, size);
	l[index].printLecturer(ofs);
}
// --------------------  main function section -------------------- 
int main() {
	system("color A");
	Doctor D("Mads", "Mikkelsen", 2015);
	Researcher R(30, 78);
	cout << " Inforamation about base class (Doctor)" << endl;
	D.printDoctror(cout); cout << endl;
	cout << " Information about base class (Researcher)" << endl;
	R.printResearcher(cout); cout << endl;

	const int N = 800;
	Lecturer* Larray = new (nothrow) Lecturer[N];
	int size = FillArray(Larray);
	sort(Larray, Larray + size, [](Lecturer& l1, Lecturer& l2) {return l1 < l2; });
	cout << " -------------------- Information about derived classes (Lecturer) -------------------- " << endl;
	for (size_t i = 0; i < size; i++)
		cout << Larray[i] << endl;

	LastTask(Larray, size);

	delete[] Larray;
	Larray = nullptr;
}

3.	აბსტრაქტული კლასი Vehicle(სატრანსპორტო საშუალება) შეიცავს მხოლოდ ორ წმინდა ვირტუალურ ფუნქციას showName და  fuel.Vehicle კლასის საფუძველზე აგებულია კონკრეტული კლასები Bus(ავტობუსი) და Trailer(ტრეილერი).კონკრეტული კლასები შეიცავენ სათანადო მონაცემებსა და კონსტრუქტორებს.ყოველ კონკრეტულ კლასში showName ფუნქციის დანიშნულებაა მანქანის სახელის(ტიპის) ბეჭდვა, ხოლო fuel ფუნქციისა – საწვავის დღიური ხარჯის გამოთვლა.
ამასთან:
ა).ავტობუსის საწვავის ხარჯი გამოითვლება როგორც წრიული მარშრუტების რაოდენობა გამრავლებული ერთი მარშრუტის გასავლელად საჭირო საწვავის ფასზე;
ბ).ტრეილერის საწვავის ხარჯი გამოითვლება როგორც საწვავის დღიური ხარჯისა  და  გარკვეულ მარაგზე ხარჯის ჯამი.
main –ში :
1)	შემოიღეთ კონკრეტული კლასების ორ–ორი ობიექტი განსხვავებული მონაცემებით.შემდეგ ყოველი კონკრეტული კლასის რომელიმე ერთი ობიექტისთვის გამოიძახეთ  showName და fuel ფუნქციები;
2)	გააკეთეთ განაცხადი პოინტერების დინამიკურ მასივზე(ან პოინტერების სხვა კონტეინერზე) სახელით v, რომელშიც შესაძლებელი იქნება  შექმნილი ობიექტების მისამართების შენახვა;
3)	შეინახეთ v–ში შექმნილი ობიექტების მისამართები, შემდეგ ერთი განმეორების(ციკლის) შეტყობინებით და  v –ს ელემენტების გამოყენებით დაბეჭდეთ  ობიექტების ინფორმაცია.



#include <iostream>
using namespace std;
// base class
class Vehicle {
	// access specifier
public:
	// pure virtual functions
	virtual void showName() const = 0;
	virtual double fuel() const = 0;
	virtual ~Vehicle() {}
};
// derived class (Bus)
class Bus : public Vehicle {
	// protected data members
protected:
	string model;
	int quantity;
	double fuel_price;
	// access specifier
public:
	// explicit value constructor
	Bus(string, int, double);
	// destrutor
	~Bus() {}
	// member function section
	double fuel()const override;
	void showName()const override;
};
// derived class (Trailer)
class Trailer : public Vehicle {
	// protected data members
protected:
	string model;
	int daily_expense;
	int supply_expense;
	// acces specifier
public:
	// explicit value constructor
	Trailer(string, int, int);
	// destructor 
	~Trailer() {}
	// member function section
	double fuel()const override;
	void showName()const override;
};
// derived class (Bus) declaration section
Bus::Bus(string m, int q, double f) : model(m), quantity(q), fuel_price(f) {}
double Bus::fuel()const { return quantity * fuel_price; }
void Bus::showName() const { cout << " -> vehicle's model : " << model << endl; }
// derived class (Trailer) declaration section
Trailer::Trailer(string m, int d, int s) : model(m), daily_expense(d), supply_expense(s) {}
double Trailer::fuel()const { return daily_expense + supply_expense; }
void Trailer::showName()const { cout << " -> vehicle's model : " << model << endl; }
int main() {
	system("color A");
	Bus B1("Ford", 20, 2.90);
	Bus B2("BMW", 30, 3);
	Trailer T1("Toyota", 50, 250);
	Trailer T2("Jaguar", 40, 160);
	B1.showName();
	cout << " -> Daily fuel consumption : " << B1.fuel() << endl << endl;

	Vehicle* v[]{ &B1,&B2,&T1,&T2 };
	cout << " ---------- Information about objects ----------" << endl;
	for (size_t i = 0; i < 4; i++)
	{
		v[i]->showName();
		cout << " -> Daily fuel consumption : " << v[i]->fuel() << endl;
	}
}













4.	მოცემულია შემდეგი კოდი
class C {
public:
	C() { cout << "C()\n"; }
	~C() { cout << "~C()\n"; }
	void print() { cout << "C\n"; }
};
class D : public C {
public:
	D() { cout << "D()\n"; }
	~D() { cout << "~D()\n"; }
	void print() { cout << "D\n"; }
};	int main()
{
	C* p0, * p1;
	p0 = new D;
	p0->print();
	delete p0;
	p1 = new C;
	p1->print();
	delete p1;
}
ა).შეასრულეთ შესაბამისი პროგრამა და ახსენით თუ რას დაბეჭდავს იგი და რატომ;
თავიდან გამოტანის ეკრანი არის  შემდეგი :
C()
D()
C
~C()
C()
C
~C()
პასუხი :  აღნიშნულ კოდის ფრაგმენტში, ვხედავთ რომ, base(C) ობიექტის ტიპის პოინტერი მიუთითებს derived(D) ტიპის ობიექტს, ასევე C ტიპის ობიექტის პოინტერი მიუთითებს C ტიპის ობიექტს.იმისათვის რომ განხორციელდეს D ტიპის ობიექტზე წვდომა C ტიპის პოინტერით, მხოლოდ საბაზო კლასზე პოინტერის(ან რეფერენსის) გამოყენებით არ ხდება, აგრეთვე, აუცილებლად საჭიროა base(C) კლასში გვქონდეს virtual(ვირტუალური)ფუნქცია.ამ შემთხვევაში, როგორც ვხედავთ არ გვაქვს მსგავსი ფუნქციები გამოყენებული ამიტომ, C ტიპის ობიექტის პოინტერს D ტიპის ობიექტზე წვდომა არ აქვს და ეს პოინტერი base ობიექტთან ამყარებს წვდომას.როგორც ვიცით, მემკვიდრე კლასის ობიექტის შექმნისას პირველად გამოიძახება წინაპარი კლასის კონსტრუქტორი შემდეგ კი მემკვიდრე კლასის კონსტრუქტორი, ხოლო დესტრუქტორები უკუ რიგით, ჯერ მემკვიდრე კლასის დესტრუქტორი და შემდეგ წინაპარი კლასის დესტრუქოტრი.აღსანიშნავია ის ფაქტიც, რომ D ობიექტის მიერ დაკავებული მეხსიერება გათავისუფლდა მხოლოდ ნაწილობრივ - ‘’განადგურდა’’ მხოლოდ C კლასის კონსტრუქტორის მიერ გამოყოფილი მეხსიერება.ამ პრობლემის გადასაჭრელად კი აუცილებელია base კლასის დესტრუქტორი უნდა იყოს ვირტუალური(virtual ~C()).
ბ).თუ პროგრამის შესრულების შედეგი, თქვენი აზრით, შეიცავს შეცდომებს, ახსენით რა ტიპისაა ეს შეცდომები და როგორ შეიძლება მათი გასწორება.ბოლოს, აჩვენეთ სწორი გამოტანის ეკრანი.
პასუხი : ზემოთ მკაფიოდ ვისაუბრე არსებულ შეცდომებზე.პირველი იყო ის, რომ აუცილებლად უნდა გვქონდეს base კლასის ვირტუალური დესტრუქტორი(რათა არ მოხდეს memory leak) და ფუნქცია.აგრეთვე საბაზო კლასის ვირტუალური ფუნქცია უნდა იყოს გადასაზღვრული(გადაფარული) მის მემკვიდრე კლასში(void print() override), რადგან პროგრამულმა კოდმა სწორად იმუშავოს.იხილეთ ქვემოთ სწორი კოდის ფრაგმენტი და გამოტანის ეკრანი :

#include <iostream>
using namespace std;
class C {
public:
	C() { cout << "C()\n"; }
	virtual ~C() { cout << "~C()\n"; }
	virtual void print() { cout << "C\n"; }
};
class D : public C {
public:
	D() { cout << "D()\n"; }
	~D() { cout << "~D()\n"; }
	void print() override { cout << "D\n"; }
};
int main()
{
	C* p0, * p1;
	p0 = new D;
	p0->print();
	delete p0;
	p1 = new C;
	p1->print();
	delete p1;
}


5.	გამონაკლისები C++ - ში: რისთვის გამოიყენება გამონაკლისები, როგორ ხდება გამონაკლისი სიტუაციის დამუშავება ? ახსენით try, catch  და throw ოპერატორების დანიშნულება გამონაკლისი სიტუაციის დამუშავებისას.
გამონაკლისი სიტუაცია - ეს არის პროგრამის შესრულების დროის შეცდომა(Run Time Error).მაგალითად, როდესაც ობიექტისთვის დინამიკური მეხსიერება არ გამოიყოფა, ამ დროს ხდება  გამონაკლისი სიტუაციის გენერირება და პროგრამის მუშაობა წყდება ავარიულად.სწორედ ამ ყველაფრის თავიდან ასაცილებლად ვიყენებთ ზემოთ აღნიშნულ სპეციფიკატორებს.გამონაკლისი სიტუაციის შესამოწმებლად კოდის ნაწილი თავსდება Try ბლოკში.თუ აღნიშნულ ბლოკში წარმოიქმნება გამონაკლისი სიტუაცია, მაშინ ეს გამონაკლისი გაიტყორცნება throw - ის  საშუალებით, Catch ბლოკში.Catch ბლოკი მართვას იღებს გასროლილი გამონაკლისი ტიპის მიხედვით.მაგალითად თუ throw გამოისვრის int ტიპის მნიშველობას, მაშინ მისი დამუშავება მოხდება catch ის მიერ, რომლის პარამეტრი იქნება int ტიპის.





სტანდარტული ტიპის რომელი გამონაკლისები იცით ? დაასახელეთ არანაკლებ სამისა და მოიყვანეთ ერთ - ერთი სტანდარტული ტიპის გამონაკლისის გამოყენების მაგალითი.
std::bad_alloc, std::bad_cast, std::bad_exception
მაგალითი :

#include <iostream> 
#include <stdexcept>
using namespace std;
int main() {
	try
	{
		int* myarray = new int[100000000000];
	}
	catch (bad_alloc& b)
	{
		cout << "bad_alloc caught: " << b.what() << endl;
	}
	return 0;
}

მოიყვანეთ გამონაკლისი სიტუაციის პროგრამული დამუშავების მაგალითი, რომელშიც throw გამოისვრის  string ტიპის გამონაკლისს.
ახსენით როგორ გამოიყენება exception კლასის ვირტუალური what()მეთოდი.

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

exception კლასის what() მეთოდი მოიცემა
virtual const char* what() const throw()
{
	return "Unknown exception";
}
როდესაც ვიძახებთ  what ფუნქციას     მაშინ  სწორედ ის  გამოიტანს იმ ბრძანებას რაც მაsში არის ჩაწერილი ამ შემთხვევაში  unknown exception.ძირითადად what   არის ფუნქცია  რომელიც გამოიყენება  შესაბამისი ბრძანების გამოსატანად exception კლასისთვის.
 
