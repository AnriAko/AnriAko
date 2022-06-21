კურსის დასახელება:    ობიექტზე ორიენტირებული დაპროგრამება 1 (C++)       კურსის  სტატუსი:   ძირითადი 
ქულების განაწილება:   1 –  8 ქულა,  2 – 14 ქულა,  3 – 9 ქულა,  4 – 4 ქულა,  5 – 5 ქულა       
ქულების ჯამი:    40 ქულა
გამოცდის ხანგრძლივობა:   3  საათი

1.	შექმენით კლასები Fridge (მაცივარი) და Bookcase (წიგნების კარადა). ყოველ კლასში შემოიღეთ: დავალების პირობის შესაბამისი private მონაცემები; უპარამეტრო კონსტრუქტორი, რომელიც ობიექტის შექმნისთანავე უზრუნველყოფს მისი მონაცემების შემოტანას კლავიატურიდან და, თუ საჭიროა, კლასის სხვა ფუნქციები. 
ასევე დაწერეთ მაცივრის და კარადის სიმაღლეების შედარების ფუნქცია ისე, რომ  იგი იყოს Bookcase კლასის ფუნქცია, ხოლო Fridge კლასის – მეგობარი ფუნქცია.   
ძირითად ფუნქციაში შექმენით ორივე კლასის თითო–თითო ობიექტი, გამოიძახეთ სიმაღლეების შედარების ფუნქცია და დაბეჭდეთ უმცირესი სიმაღლის მქონე ობიექტის მოცულობა. თუ სიმაღლეები ტოლია, დაბეჭდეთ მაცივრის სიგანე, ფერი და ფასი. 

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
		<< " -> Fridge's price is : "<< price << endl << endl;
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
bool Bookcase::compare(const Fridge& F) { 
	int result;
	if (height < F.height)
		result = 1;
	else if(height > F.height)
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







2.	ააგეთ კლასების შემდეგი იერარქია: 
ა).   საბაზო Doctor (მეცნიერებათა დოქტორი) კლასის მონაცემებია firstName (სახელი), lastName (გვარი) და thesis (დისერტაციის დაცვის წელი);  კლასის ფუნქციებია – პარამეტრებიანი კონსტრუქტორი, დესტრუქტორი  და სხვა ფუნქციები საჭიროების მიხედვით;
ბ).  მეორე საბაზო Researcher (მკვლევარი) კლასის მონაცემებია publications (პუბლიკაციების რაოდენობა) და projects (პროექტების რიცხვი);  კლასის ფუნქციებია – პარამეტრებიანი კონსტრუქტორი, დესტრუქტორი  და სხვა ფუნქციები საჭიროების მიხედვით;
გ).  ორივე კლასის მემკვიდრე Lecturer (ლექტორი) კლასში დაამატეთ მონაცემები highSchool (უმაღლესი სკოლის დასახელება) და courses (ჩატარებული კურსების რიცხვი), შემოიღეთ პარამეტრებიანი კონსტრუქტორი, დესტრუქტორი  და სხვა ფუნქციები საჭიროების მიხედვით. კლასის ობიექტისთვის გადატვირთეთ  >>  და  <<  ოპერატორები. ასევე გადატვირთეთ  <  ოპერატორი როგორც  Lecturer კლასის ფუნქცია.
main -ში  შეასრულეთ შემდეგი დავალებები:
1)   შექმენით Doctor და Researcher კლასების თითო-თითო სტატიკური ობიექტი რაიმე კონკრეტული მნიშვნელობებით და შემდეგ დაბეჭდეთ ინფორმაცია მათ შესახებ;  
2)   გააკეთეთ განაცხადი ლექტორების დინამიკურ მასივზე და შეავსეთ იგი მონაცემებით teachers.txt ფაილიდან. ლექტორების რაოდენობა არ აღემატება 800–ს.   
სტანდარტული sort ალგორითმის და გადატვირთული < ოპერატორის გამოყენებით დაალაგეთ  ლექტორების მასივი პუბლიკაციების რაოდენობის კლებადობის მიხედვით. დალაგებული მასივი დაბეჭდეთ ეკრანზე. 
შემდეგ დაწერეთ კოდის ფრაგმენტი, რომელიც reference.txt ფაილში დაბეჭდავს იმ ლექტორების მონაცემებს, რომელთა პუბლიკაციების რიცხვი არის უმცირესი,  უდიდესი,  და  ყველაზე  ახლოს ყველა ლექტორის პუბლიკაციების საშუალო  რაოდენობასთან. 
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
	Lecturer(string,string, int,int,int,string,int);
	// destructor
	~Lecturer();
	// member function section
	void printLecturer(ostream&)const;
	int get_Publications()const;
	// overloading function section
	friend istream& operator >> (istream&,Lecturer&);
	friend ostream& operator << (ostream&, const Lecturer&);
	bool operator < (const Lecturer&);
};
// -------------------- base class (Doctor) declaration section --------------------
Doctor::Doctor() {}
Doctor::Doctor(string f, string l, int t) : firstName(f), lastName(l), thesis(t) {}
void Doctor::printDoctror(ostream& out)const {
	out << " -> firstName - " << firstName << endl
		<< " -> lastName - " << lastName << endl
		<< " -> thesis - " << thesis << endl;
}
Doctor :: ~Doctor() = default;
// -------------------- base class (Researcer) declaration section --------------------
Researcher::Researcher() {}
Researcher::Researcher(int p, int pr) : publications(p), projects(pr) {}
void Researcher::printResearcher(ostream& out)const {
	out << " -> publications - " << publications << endl
		<< " -> projects - " << projects << endl;
}
Researcher :: ~Researcher() = default;
// -------------------- derived class (Lecturer) declaration section --------------------
Lecturer::Lecturer() {}
Lecturer::Lecturer(string f, string l, int t, int p, int pr, string h, int c): Doctor(f, l, t), Researcher(p, pr), courses(c), highSchool(h) {}
Lecturer :: ~Lecturer() {}
istream& operator >>(istream& in, Lecturer& l)
{
	return in >> l.firstName >> l.lastName >> l.thesis >> l.publications >> l.projects >> l.highSchool >> l.courses;
}
void Lecturer::printLecturer(ostream& out)const
{
	printDoctror(out);
	printResearcher(out);
	out << " -> Highschool - " << highSchool << endl
		<< " -> courses - " << courses << endl;
}
ostream& operator <<(ostream& out,const Lecturer& l)
{
	l.printLecturer(out);
	return out;
}
bool Lecturer :: operator < (const Lecturer& l) {
	return this->publications > l.publications;
}
int Lecturer::get_Publications()const { return publications; }
// -------------------- global function --------------------
int FillArray(Lecturer* l)
{
	int counter = 0;
	ifstream ifs("teachers.txt");
	while (!ifs.eof())
	{
		ifs >> l[counter++];
	}
	return counter;
}
int getNearestIndex(Lecturer* l, int size) {
	int sum = 0, index = 0,average = 0;
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
		return index ;
	return (index + 1);
}
void LastTask(Lecturer* l, int size)
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
	sort(Larray, Larray + size, []( Lecturer& l1, Lecturer& l2) {return l1 < l2; });
	cout << " -------------------- Information about derived classes (Lecturer) -------------------- " << endl;
	for (size_t i = 0; i < size; i++)
		cout << Larray[i] << endl;

	LastTask(Larray,size);

	delete[] Larray;
	Larray = nullptr;
}

3.	აბსტრაქტული კლასი Vehicle (სატრანსპორტო საშუალება) შეიცავს მხოლოდ ორ წმინდა ვირტუალურ ფუნქციას showName და  fuel. Vehicle კლასის საფუძველზე აგებულია კონკრეტული კლასები Bus (ავტობუსი) და Trailer (ტრეილერი). კონკრეტული კლასები შეიცავენ სათანადო მონაცემებსა და კონსტრუქტორებს. ყოველ კონკრეტულ კლასში showName ფუნქციის დანიშნულებაა მანქანის სახელის (ტიპის) ბეჭდვა, ხოლო fuel ფუნქციისა – საწვავის დღიური ხარჯის გამოთვლა.  
ამასთან:                         
  ა).   ავტობუსის საწვავის ხარჯი გამოითვლება როგორც წრიული მარშრუტების რაოდენობა გამრავლებული ერთი მარშრუტის გასავლელად საჭირო საწვავის ფასზე;
  ბ).   ტრეილერის საწვავის ხარჯი გამოითვლება როგორც საწვავის დღიური ხარჯისა  და  გარკვეულ მარაგზე ხარჯის ჯამი.
main –ში: 
1)	შემოიღეთ კონკრეტული კლასების ორ–ორი ობიექტი განსხვავებული მონაცემებით. შემდეგ ყოველი კონკრეტული კლასის რომელიმე ერთი ობიექტისთვის გამოიძახეთ  showName და fuel ფუნქციები;
2)	გააკეთეთ განაცხადი პოინტერების დინამიკურ მასივზე (ან პოინტერების სხვა კონტეინერზე) სახელით v, რომელშიც შესაძლებელი იქნება  შექმნილი ობიექტების მისამართების შენახვა; 
3)	შეინახეთ v–ში შექმნილი ობიექტების მისამართები, შემდეგ ერთი განმეორების (ციკლის) შეტყობინებით და  v –ს ელემენტების გამოყენებით დაბეჭდეთ  ობიექტების ინფორმაცია.



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
Bus :: Bus(string m, int q, double f) : model(m), quantity(q), fuel_price(f) {}
double Bus::fuel()const {	return quantity * fuel_price;}
void Bus::showName() const {	cout << " -> vehicle's model : " << model << endl;}
// derived class (Trailer) declaration section
Trailer::Trailer(string m, int d, int s) : model(m), daily_expense(d), supply_expense(s) {}
double Trailer::fuel()const {	return daily_expense + supply_expense;}
void Trailer::showName()const { cout << " -> vehicle's model : " << model << endl;}
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
C * p0, *p1;
p0 = new D;
p0->print();
delete p0;
p1 = new C;
p1->print();
delete p1;
}
        ა).   შეასრულეთ შესაბამისი პროგრამა და ახსენით თუ რას დაბეჭდავს იგი და რატომ;
თავიდან გამოტანის ეკრანი არის  შემდეგი:
 C()
D()
C
~C()
C()
C
~C()
პასუხი :  აღნიშნულ კოდის ფრაგმენტში, ვხედავთ რომ, base (C) ობიექტის ტიპის პოინტერი მიუთითებს derived (D) ტიპის ობიექტს, ასევე C ტიპის ობიექტის პოინტერი მიუთითებს C ტიპის ობიექტს. იმისათვის რომ განხორციელდეს D ტიპის ობიექტზე წვდომა C ტიპის პოინტერით, მხოლოდ საბაზო კლასზე პოინტერის (ან რეფერენსის) გამოყენებით არ ხდება,აგრეთვე,აუცილებლად საჭიროა base  (C) კლასში გვქონდეს virtual(ვირტუალური) ფუნქცია. ამ შემთხვევაში, როგორც ვხედავთ არ გვაქვს მსგავსი ფუნქციები გამოყენებული ამიტომ, C ტიპის ობიექტის პოინტერს D ტიპის ობიექტზე წვდომა არ აქვს და ეს პოინტერი base ობიექტთან ამყარებს წვდომას.როგორც ვიცით,მემკვიდრე კლასის ობიექტის შექმნისას პირველად გამოიძახება წინაპარი კლასის კონსტრუქტორი შემდეგ კი მემკვიდრე კლასის კონსტრუქტორი,ხოლო დესტრუქტორები უკუ რიგით, ჯერ მემკვიდრე კლასის დესტრუქტორი და შემდეგ წინაპარი კლასის დესტრუქოტრი.აღსანიშნავია ის ფაქტიც, რომ D ობიექტის მიერ დაკავებული მეხსიერება გათავისუფლდა მხოლოდ ნაწილობრივ - ‘’განადგურდა’’ მხოლოდ C კლასის კონსტრუქტორის მიერ გამოყოფილი მეხსიერება. ამ პრობლემის გადასაჭრელად კი აუცილებელია base კლასის დესტრუქტორი უნდა იყოს ვირტუალური(virtual ~C()).
        ბ).   თუ პროგრამის შესრულების შედეგი, თქვენი აზრით, შეიცავს შეცდომებს, ახსენით რა ტიპისაა ეს შეცდომები და როგორ შეიძლება მათი გასწორება. ბოლოს, აჩვენეთ სწორი გამოტანის ეკრანი.
პასუხი : ზემოთ მკაფიოდ ვისაუბრე არსებულ შეცდომებზე. პირველი იყო ის , რომ აუცილებლად უნდა გვქონდეს base კლასის ვირტუალური დესტრუქტორი (რათა არ მოხდეს memory leak) და ფუნქცია. აგრეთვე საბაზო კლასის ვირტუალური ფუნქცია უნდა იყოს გადასაზღვრული (გადაფარული) მის მემკვიდრე კლასში (void print() override),რადგან პროგრამულმა კოდმა სწორად იმუშავოს . იხილეთ ქვემოთ სწორი კოდის ფრაგმენტი და გამოტანის ეკრანი:

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
 

5.	გამონაკლისები C++-ში: რისთვის გამოიყენება გამონაკლისები, როგორ ხდება გამონაკლისი სიტუაციის დამუშავება? ახსენით try, catch  და throw ოპერატორების დანიშნულება გამონაკლისი სიტუაციის დამუშავებისას. 
   გამონაკლისი სიტუაცია - ეს არის პროგრამის შესრულების დროის შეცდომა( Run Time Error). მაგალითად, როდესაც ობიექტისთვის დინამიკური მეხსიერება არ გამოიყოფა, ამ დროს ხდება  გამონაკლისი სიტუაციის გენერირება და პროგრამის მუშაობა წყდება ავარიულად. სწორედ ამ ყველაფრის თავიდან ასაცილებლად ვიყენებთ ზემოთ აღნიშნულ სპეციფიკატორებს. გამონაკლისი სიტუაციის შესამოწმებლად კოდის ნაწილი თავსდება Try ბლოკში.თუ აღნიშნულ ბლოკში წარმოიქმნება გამონაკლისი სიტუაცია,მაშინ ეს გამონაკლისი გაიტყორცნება throw-ის  საშუალებით,  Catch ბლოკში. Catch ბლოკი მართვას იღებს გასროლილი გამონაკლისი ტიპის მიხედვით. მაგალითად თუ throw გამოისვრის int ტიპის მნიშველობას, მაშინ მისი დამუშავება მოხდება catch ის მიერ, რომლის პარამეტრი იქნება int ტიპის.





სტანდარტული ტიპის რომელი გამონაკლისები იცით? დაასახელეთ არანაკლებ სამისა და მოიყვანეთ ერთ-ერთი სტანდარტული ტიპის გამონაკლისის გამოყენების მაგალითი.
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
როდესაც ვიძახებთ  what ფუნქციას     მაშინ  სწორედ ის  გამოიტანს იმ ბრძანებას რაც მაsში არის ჩაწერილი ამ შემთხვევაში  unknown exception. ძირითადად what   არის ფუნქცია  რომელიც გამოიყენება  შესაბამისი ბრძანების გამოსატანად exception კლასისთვის.

	კურსის დასახელება:    ობიექტზე ორიენტირებული დაპროგრამება 1 (C++)         კურსის  სტატუსი:   ძირითადი
ქულების განაწილება:   1 –  8 ქულა,  2 – 14 ქულა,  3 – 9 ქულა,  4 – 4 ქულა,   5 – 5 ქულა.        	       
ქულების ჯამი:    40 ქულა.
გამოცდის ხანგრძლივობა:   3  საათი.

1.	შექმენით კლასები Minibus (მიკროავტობუსი) და Car (ავტომობილი). ყოველ კლასში შემოიღეთ: დავალების პირობის შესაბამისი private მონაცემები; უპარამეტრო კონსტრუქტორი, რომელიც ობიექტის შექმნისთანავე უზრუნველყოფს მისი მონაცემების შემოტანას კლავიატურიდან და, თუ საჭიროა, კლასის სხვა ფუნქციები. 
ასევე დაწერეთ მანქანების სიჩქარეების შეადარების ფუნქცია ისე, რომ  იგი იყოს  Car კლასის ფუნქცია, ხოლო Minibus კლასის – მეგობარი ფუნქცია.
ძირითად ფუნქციაში შექმენით ორივე კლასის თითო–თითო ობიექტი, გამოიძახეთ სიჩქარეების შედარების ფუნქცია და დაბეჭდეთ იმ მანქანის მოცულობა, რომელსაც მეტი სიჩქარე აქვს. თუ სიჩქარეები ტოლია, დაბეჭდეთ მიკროავტობუსის წონა, ფერი და მგზავრების რაოდენობა. 

#include <iostream>
#include <string>
using namespace std;

class Car;

class Minibus
{
	double speed;
	string name;
	int passengers;
	double weight;
	string colour;
	int volume;
public:
	Minibus()
	{
		cout << "Minibus name - "; cin >> name;
		cout << "Minibus speed (km/h) - "; cin >> speed;
		cout << "Amount of passengers - "; cin >> passengers;
		cout << "Minibus weight (kg) - "; cin >> weight;
		cout << "Minibus colour - "; cin >> colour;
		cout << "Minibus volume - "; cin >> volume;
		cout << endl << endl;
	}
	~Minibus() {}
	double getWeight() { return weight; }
	int getPassengers() { return passengers; }
	string getColor() { return colour; }
	int getVolume() { return volume; }
	unsigned int max(Car&);
};

class Car
{
	double speed;
	string name;
	double weight;
	string colour;
	int volume;
public:
	Car()
	{
		cout << "Car name - "; cin >> name;
		cout << "Car speed (km/h) -"; cin >> speed;
		cout << "Car weight (kg) - "; cin >> weight;
		cout << "Car color - "; cin >> colour;
		cout << "Car volume - "; cin >> volume;
		cout << endl << endl;
	}
	~Car() {}
	int getVolume() { return volume; }
	friend unsigned int Minibus::max(Car&);
};

unsigned int Minibus::max(Car& C)
{
	if (this->speed > C.speed)return 1;
	else if (this->speed < C.speed)return 2;
	else return 3;
}

int main()
{
	Minibus M;
	Car C;
	int N = M.max(C);
	if (N == 1)cout << "Minibus volume is: " << M.getVolume() << endl;
	else if (N == 2)cout << "Car volume is: " << C.getVolume() << endl;
	else cout << "Minibus:\nWeight-" << M.getWeight() <<" kg."<< "\nColour - "
		<< M.getColor() << "\nPassengers - " << M.getPassengers() << endl;
}


2.	ააგეთ კლასების შემდეგი იერარქია: 
ა).     საბაზო Population (მოსახლეობა) კლასის მონაცემებია number (მოსახლეობის რაოდენობა, მლნ.) და density (მოსახლეობის სიმჭიდროვე, ად/კმ2);  კლასის ფუნქციებია – პარამეტრებიანი კონსტრუქტორი, დესტრუქტორი და სხვა ფუნქციები საჭიროების მიხედვით; 
ბ).   მეორე საბაზო Territory (ტერიტორია) კლასის მონაცემებია area (ფართობი, კვ.კმ) და city (ქალაქების რიცხვი);  კლასის ფუნქციებია – პარამეტრებიანი კონსტრუქტორი, დესტრუქტორი  და სხვა ფუნქციები საჭიროების მიხედვით;
გ).     ორივე კლასის მემკვიდრე Country (ქვეყანა) კლასში დაამატეთ მონაცემები name (ქვეყნის სახელი) და language (ოფიციალური ენა); შემოიღეთ პარამეტრებიანი კონსტრუქტორი, დესტრუქტორი და სხვა ფუნქციები საჭიროების მიხედვით. კლასის ობიექტისთვის გადატვირთეთ  >>  და  <<  ოპერატორები.  ასევე გადატვირთეთ  <  ოპერატორი როგორც  Country  კლასის ფუნქცია.
main -ში  შეასრულეთ შემდეგი დავალებები:
1)  შექმენით Population და Territory კლასების თითო-თითო სტატიკური ობიექტი რაიმე კონკრეტული მნიშვნელობებით და შემდეგ დაბეჭდეთ ინფორმაცია მათ შესახებ; 
2)  გააკეთეთ განაცხადი ქვეყნების დინამიკურ მასივზე და ჩაწერეთ მასში ქვეყნების მონაცემები countries.txt ფაილიდან. ქვეყნების რაოდენობა არ აღემატება 100–ს. 
სტანდარტული sort ალგორითმის და გადატვირთული < ოპერატორის გამოყენებით დაალაგეთ ქვეყნების მასივი მოსახლეობის სიმჭიდროვის ზრდადობის მიხედვით. დალაგებული მასივი დაბეჭდეთ ეკრანზე.
შემდეგ დაწერეთ კოდის ფრაგმენტი, რომელიც out.txt ფაილში დაბეჭდავს იმ ქვეყნების მონაცემებს, რომელთა მოსახლეობის სიმჭიდროვე არის უდიდესი, უმცირესი და  ყველაზე  ახლოს ყველა ქვეყნის საშუალო სიმჭიდროვესთან. 
ბოლოს, გაათავისუფლეთ დაკავებული დინამიკური მეხსიერება. 

#include<iostream>
#include<fstream>
#include<algorithm>
using namespace std;

class Population
{
protected:
	int  number;
	int density; // Density of population.
public:
	Population() {}
	Population(int number, int density)
	{
		this->number = number;
		this->density = density;
	}
	~Population() {}
	void show()
	{
		cout << "Number - " << number
			<< "\nDensity -  " << density;
	}
	int getDensity() { return density; }
};

class Territory
{
protected:
	int area; // (square km)
	int city;
public:
	Territory() {}
	Territory(int area, int city)
	{
		this->area = area;
		this->city = city;
	}
	~Territory() {}
	void show()
	{
		cout << "\nArea - " << area
			<< "\nCity - " << city << endl;
	}
};

class Country :public Population, public Territory
{
	string name;
	string language;
public:
	Country() {}
	Country(int number, int density, int area, int city, string name, string language)
		:Population(number, density), Territory(area, city)
	{
		this->name = name;
		this->language = language;
	}
	friend istream& operator>>(istream& in, Country& C);
	friend ostream& operator<<(ostream& out, Country& C);
	bool operator <(Country& C)
	{
		return this->density < C.density;
	}
};
istream& operator>>(istream& in, Country& C)
{
	cout << "Number-"; in >> C.number;
	cout << "Density-"; in >> C.density;
	cout << "Area-"; in >> C.area;
	cout << "City-"; in >> C.city;
	cout << "Name-"; in >> C.name;
	cout << "Language-"; in >> C.language;
	return in;
}
ostream& operator<<(ostream& out, Country& C)
{
	out << "Number" << C.number
		<< "\nDensity-" << C.density
		<< "\nArea-" << C.area
		<< "\nCity-" << C.city
		<< "\nName-" << C.name
		<< "\nLanguage-" << C.language;
	return out;
}
int main()
{
	static Population P(90, 8000);
	static Territory T(6500, 9000);
	cout << "Population\n";
	P.show();
	cout << "\nTerritory\n";
	T.show();
	ifstream fin("countries.txt");
	Country* C = new(nothrow) Country[100];
	int size = 0;
	while (fin)
	{
		fin >> C[size];
		size++;
	}
	sort(C, C + size);
	for (int i(0); i < size; i++)
	{
		cout << C[i] << endl << endl;
	}
	ofstream fout("out.txt");
	int sum(0);
	int average;
	for (int i(0); i < size; i++)
	{
		sum += C[i].getDensity();
	}
	average = sum / size;
	int avNum;
	for (int i(1); i < size; i++)
	{
		if (average >= C[i - 1].getDensity() && average <= C[i].getDensity())
		{
			if ((average - C[i - 1].getDensity()) < C[i].getDensity())
			{
				avNum = i - 1;
			}
			else
			{
				avNum = i;
			}
		}
	}
	fout << "Smallest - " << C[1] << endl
		<< "Close to - " << C[avNum] << endl
		<< "Biggest - " << C[size - 1];
}
3.	აბსტრაქტული კლასი Employee (თანამშრომელი) შეიცავს მხოლოდ ორ წმინდა ვირტუალურ ფუნქციას printStatus და salary. Employee კლასის საფუძველზე აგებულია კონკრეტული კლასები Staff  (შტატის თანამშრომელი) და HourlyWorker (საათობრივად მოწვეული თანამშრომელი). კონკრეტული კლასები შეიცავენ სათანადო მონაცემებსა და კონსტრუქტორებს. ყოველ კონკრეტულ კლასში  printStatus ფუნქციის დანიშნულებაა თანამშრომლის სტატუსის (ტიპის) ბეჭდვა, ხოლო salary ფუნქციისა –  მისი თვიური ხელფასის გამოთვლა.  
   ამასთან:                              
ა).   შტატის თანამშრომელი ღებულობს ფიქსირებულ თვიურ ხელფასს და კიდევ გარკვეულ დანამატს;  
ბ).  საათობრივად მოწვეული თანამშრომლის ხელფასი გამოითვლება როგორც ერთ საათში შექმნილი პროდუქციის ღირებულება გამრავლებული მუშა საათებზე.
main  –ში:
1)	შექმენით კონკრეტული კლასების ორ–ორი ობიექტი განსხვავებული მონაცემებით. შემდეგ ყოველი კონკრეტული კლასის რომელიმე ერთი ობიექტისთვის გამოიძახეთ printStatus და  salary ფუნქ-ციები;
2)	გააკეთეთ განაცხადი პოინტერების დინამიკურ მასივზე (ან პოინტერების სხვა კონტეინერზე) სახელით x,  რომელშიც შესაძლებელი იქნება შექმნილი ობიექტების მისამართების შენახვა; 
3)	x –ში შეინახეთ შექმნილი ობიექტების მისამართები, შემდეგ ერთი განმეორების (ციკლის) შეტყობინებით და x –ის ელემენტების გამოყენებით დაბეჭდეთ  ობიექტების ინფორმაცია.

#include <iostream>
#include <vector>
using namespace std;
class Employee {
public:
	virtual void printStatus() = 0;
	virtual int Salary() = 0;
};
class Staff : public Employee {
	double salary, plus;
public:
	Staff(double salary, double plus) : salary(salary), plus(plus) {}
	void printStatus()override {
		cout << "Staff" << endl;
	}
	int Salary()override {
		return salary + plus;
	}
};
class hourlyWorker : public Employee {
	double price;
	int hour;
public:
	hourlyWorker(double price, int hour) : price(price), hour(hour) {}
	void printStatus()override {
		cout << "hourlyWorker" << endl;
	}
	int Salary()override {
		return price * hour;
	}
};

int main() {
	Staff s1(100, 200);
	Staff s2(20, 300);
	hourlyWorker h1(11, 354);
	hourlyWorker h2(123, 233);
	s1.printStatus();
	cout << s1.Salary() << endl;
	h1.printStatus();
	cout << h1.Salary() << endl;
	vector<Employee*> emp{ &s1,&s2,&h1,&h2 };
	for (int i = 0; i < 4; i++) {
		emp[i]->printStatus();
		cout << emp[i]->Salary() << endl;
	}
}

4.	მოცემულია შემდეგი კოდი
class B{
  public:
     B(){ cout << "B()\n"; }
     virtual ~B(){ cout << "~B()\n"; }
     void print(){cout << "B\n";}
};
class D: public B{
  public:
     D(){ cout << "D()\n"; }
     ~D(){ cout << "~D()\n"; }
     void print(){cout << "D\n";}
};	int main() 
{
   B * p0, *p1;
   p0 = new B;
   p0->print(); 
   delete p0;
   p1 = new D;  
   p1->print();
   delete p1;
}

        ა).   შეასრულეთ შესაბამისი პროგრამა და ახსენით თუ რას დაბეჭდავს იგი და რატომ;
B() ბეჭდავს B კლასის დეფოლტ კონსტრუქტორს
B        მუშაობს ბეჭდვის ფუნქცია
~B() ბეჭდავს Bკლასის დესტრუქტორს (დეფოლტ)
B()    ბეჭდავს B კლასის დეფოლტ კონსტრუქტორს
D()     ბეჭდავს D კლასის დეფოლტ კონსტრუქტორს
B         მუშაობს ბეჭდვის ფუნქცია
~D() ბეჭდავს D კლასის დესტრუქტორს (დეფოლტ)
~B() ბეჭდავს B კლასის დესტრუქტორს (დეფოლტ)
        ბ).   თუ პროგრამის შესრულების შედეგი, თქვენი აზრით, შეიცავს შეცდომას, ახსენით რა ტიპისაა ეს შეცდომა და როგორ შეიძლება მისი გასწორება. ბოლოს, აჩვენეთ სწორი გამოტანის ეკრანი.
void print() { cout << "D\n"; } არ იბეჭდებოდა ეკრანზე, რის გამოც ცოტათი შევხვალე main.
/* 
B()
B
~B()
B()
D()
D
~D()
~B()
*/
5.	რა დანიშნულება აქვს კლასის  თარგის (template) გამოყენებას? 
რა შემთხვევაშია მიზანშეწონილი ფუნქცია–თარგის შექმნა?
პასუხი: თარგი - არის მარტივი და თან იმავდროულად საკმაოდ ძლიერი ხელსაწყო C++ ენაში. მისი იდეა მარტივია: გადასცეს მონაცემთა ტიპი პარამეტრის სახით ისე, რომ ჩვენ არ მოგვიწიოს ერთი და იმავე კოდის წერა მონაცემთა სხვადასხვა ტიპებისთვის. მაგალითად, კომპანიამ პროგრამული უზრუნველყოფის დეველოპერს შესაძლოა მოთხოვოს sort() სხვადასხვა მონაცემთა ტიპებისთვის. იმის მაგივრად, რომ ვწეროთ რამდენიმე კოდი ჩვენ შეგვიძლია დავწეროთ sort() ერთხელ და გადავცეთ მონაცემთა ტიპი პარამეტრის სახით.
C++ ენაში არსებობს ორი ძირითადი საკვანძო სიტყვა თარგის გამოსაყენებლად, ესენია: <template> და <typename>. მეორე სიტყვის შეცვლა ყოველთვის შეგვიძლია საკვანძო სიტყვით <class>.
თარგი მუშაობს შემდეგნაირად: იგი ფართოვდება კომპილაციისას. ეს პროცესი ჰგავს მაკროსებს. განსხვავება იმაშია, რომ კომპილერი ამოწმებს ტიპებს თარგის გაფართოებამდე. იდეა მარტივია, კოდი თავდაპირველად შოიცავს, მხოლოდ, ფუნქციას/კლასს, ხოლო დაკომპილირებული კოდი შეიძლება შეიცავდეს რამდენიმე კოპიას ერთი და იმავე ფუნქციის/კლასის. ფუნქცია თარგის გამოყენებისას ჩვენ ვიყენებთ მის ძირითად ვარიაციას, რომელიც შეგვიძლია გამოვიყენოთ სხვადასხვა მონაცემთა ტიპებისთვის, როგორებიცაა: sort(), max(), min(), printArray(), swap(), count(), count_if()…

შექმენით ფუნქცია–თარგი, რომელიც როგორც მთელი, ისე ნამდვილი რიცხვების ვექტორისთვის გამოითვლის და დააბრუნებს მისი ელემენტების ჯამის მეხუთედს. ვექტორი გადაეცით ფუნქციას ეფექტურად და უსაფრთხოდ. 
მოიყვანეთ ამ ფუნქციის გამოყენების მაგალითი:  

#include<iostream>
#include<vector>
using namespace std;
template <typename T>
T sum(const vector<T>& vec)
{
	T S = 0;
	for (auto x : vec)
	{
		S += x;
	}
	return S / 5;
}
int main() {
	vector<int>vec{ 1,2,3,4,5,6,7 };
	cout << sum(vec) << endl;
	vector<double>vec1{ 1.2, 2.3, 3.3, 5, 3.3 ,5.6,1,2,5 };
	cout << sum(vec1);
}


ძირითად ფუნქციაში გააკეთეთ განაცხადი მთელი რიცხვების ვექტორზე, განაცხადისთანავე ჩაწერეთ ვექტორში 7 მთელი რიცხვი, გამოიძახეთ შექმნილი ფუნქცია და დაბეჭდეთ შედეგი. შემდეგ გააკეთეთ განაცხადი ნამდვილების ვექტორზე, განაცხადისთანავე ჩაწერეთ მასში 8 ნამდვილი რიცხვი და დაბეჭდეთ ფუნქციის მუშაობის შედეგი. შედეგების ბეჭდვას თან დაურთეთ სათანადო გზავნილები.

//  კოდია, რომელშიც რამდენიც გვინდა იმდენ ელემენტს შევიტანთ
#include <iostream>
#include <vector>
using namespace std;
template <typename P>
void printVector(const vector <P> & x)
{
	for (P el : x)
	cout << el << ' ';
	cout << endl;
}
template <typename In>
void inputVector(vector <In> & x)
{
	int i(0);
	In value;
	while (cin >> value)
		x.push_back(value);
    cin.clear();
	cin.ignore();
}

int main()
{
	vector <int> ints;
	cout << "Enter ints separated by space and end by using Ctrl+Z.\n";
	inputVector(ints);
	printVector(ints);
	vector<double > doubles;
	cout << "Enter doubles separated by space and end by using Ctrl+Z.\n";
	inputVector(doubles);
	printVector(doubles);
}


