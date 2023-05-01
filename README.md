Download Link: https://assignmentchef.com/product/solved-ceng242-programming-exam-6
<br>
<h1>1             Problem Definition</h1>

In your second programming examination for C<sup>++</sup>, you are going to implement a real estate agency simulation. There will be owners to buy and sell their properties and properties to be owned.

<h2>1.1            General Specifications</h2>

<ul>

 <li>The signatures of the functions, their explanations and specifications are given in the following section. Read them carefully.</li>

 <li>Make sure that your implementations comply with the function signatures.</li>

 <li>You may define any number of helper function(s) as you need.</li>

 <li>You are not allowed to import any <em>extra </em>library for this exam.</li>

 <li>You should NOT make any change in header files. Those given to you will not be used in evaluation process.</li>

</ul>

<h2>1.2            Quick VPL Tips (In case you’ve forgotten them!)</h2>

<ul>

 <li>Evaluation is fast. If evaluation seems to hang for more than a few seconds, your code is entering an infinite loop or has an abnormal algorithmic complexity. Or you’ve lost your connection, which is <em>much </em>less likely!</li>

 <li>Although the run console does not support keyboard shortcuts, it should still be possible to copy and paste using the right-click menu (Tested on latest versions of Firefox and Chrome).</li>

 <li>Get familiar with the environment. Press the plus shapes button on the top-left corner to see all the options. You can download/upload files, change your font and theme, switch to fullscreen etc. Useful stuff!</li>

</ul>

<h1>2             Real Estate Agency</h1>

There are two base classes in this programming exam:

<ul>

 <li>Owner</li>

 <li>Property</li>

</ul>

<h2>2.1            Owner</h2>

Owner Class Properties

<table width="673">

 <tbody>

  <tr>

   <td width="673">class Owner{ …protected:std::string name; float balance; std::vector&lt;Property *&gt; properties;};</td>

  </tr>

 </tbody>

</table>

Each owner has a name, a balance value and the list of properties owned. There are 2 classes derived from Owner class:

<ul>

 <li>Person</li>

 <li>Corporation</li>

</ul>

These two classes differ from each other buy their class properties. Person class has age property while Corporation class has address information.

Person and Corporation Class Properties

<table width="673">

 <tbody>

  <tr>

   <td width="673">class Person : public Owner{ private: int age; …};class Corporation : public Owner{ private: std::string address; …};</td>

  </tr>

 </tbody>

</table>

Person/Corporation instances may own any number of properties. They can sell a property if they own that property and they can buy a property if they can afford it.

Constructors of these derived classes are as follows:

Person and Corporation Class Constructors

<table width="673">

 <tbody>

  <tr>

   <td width="339">Person(const std::string &amp;name, float</td>

   <td width="334">balance, int age);</td>

  </tr>

  <tr>

   <td width="339">Corporation(const std::string &amp;name,</td>

   <td width="334">float balance, std::string address);</td>

  </tr>

 </tbody>

</table>

There are 6 functions of these classes to be implemented:

<ul>

 <li>void print_info(): prints name and age of the owner if it is a person, prints name and address of the owner if it is a corporation.</li>

</ul>

If Person:

Name: &lt;name&gt; Age: &lt;age&gt; If Corporation:

Name: &lt;name&gt; Address: &lt;age&gt;

<ul>

 <li>std::string get_name(): returns the name of the owner.</li>

 <li>void add_property(Property *property): takes a property pointer and adds it to the property list of the owner.</li>

 <li>void buy(Property *property, Owner *seller): takes a property pointer and an owner pointer describing the seller. If the seller has corresponding estate and this owner has enough money to buy this property, property will be sold to this owner. Property lists and balance values of the buyer and seller will be updated. At the beginning of the transaction, operation is printed as:</li>

</ul>

[BUY] Property: &lt;name of the property&gt; Value: &lt;value of the property&gt; &lt;Seller&gt;—&gt;&lt;Buyer&gt;

<ul>

 <li>void sell(Property *property, Owner *buyer): takes a property pointer and an owner pointer describing the buyer. If this owner has corresponding estate and the buyer has enough money to buy this property, property will be sold to buyer. Property lists and balance values of buyer and seller will be updated. At the beginning of the transaction, operation is printed as:</li>

</ul>

[SELL] Property: &lt;name of the property&gt; Value: &lt;value of the property&gt; &lt;Seller&gt;—&gt;&lt;Buyer&gt;

<ul>

 <li>void list_properties(): prints the balance value and the list of properties.</li>

</ul>

Properties of &lt;name&gt;:

Balance: &lt;balance&gt;$

<ol>

 <li>&lt;name of the property-1&gt;</li>

 <li>&lt;name of the property-2&gt; …</li>

 <li>&lt;name of the property-n&gt;</li>

</ol>

2.1.1          Unsuccessful Transactions

When making a transaction (buy/sell), it is first checked whether the buyer has sufficient balance. If the buyer does not have enough money: [ERROR] Unaffordable property text is printed.

Note: There are two whitespaces between Unaffordable and property words.

If the buyer has enough money, it is checked whether the seller owns the property. If the seller is not the owner of the property:

[ERROR] Transaction on unowned property text is printed.

Note: There are two whitespaces between Transaction, on, unowned, and property words.

<h2>2.2            Property</h2>

Property Class Properties

<table width="673">

 <tbody>

  <tr>

   <td width="673">class Property{ …protected: std::string property_name; int area;Owner *owner;};</td>

  </tr>

 </tbody>

</table>

Each property has a name, an area value and the owner information. There are 3 classes derived from Property class:

<ul>

 <li>Villa</li>

 <li>Apartment</li>

 <li>Office</li>

</ul>

These three classes differ from each other buy their class properties. Villa Class includes the information of how many floors it has and whether it has a garden or not. The Apartment Class, on the other hand, keeps the information on which floor it is and whether there is an elevator. Finally, Office Class includes information on whether there is a provided Wi-fi and reception service.

Villa, Apartment, Office Class Properties

<table width="673">

 <tbody>

  <tr>

   <td width="673">class Villa : public Property{ private:int number_of_floors; bool having_garden; …};class Apartment : public Property{ private:int floor; bool having_elevator; …};class Office : public Property{ private:bool having_wifi; bool having_reception; …};</td>

  </tr>

 </tbody>

</table>

Constructors of these derived classes are as follows: Villa, Apartment and Office Class Constructors

<table width="673">

 <tbody>

  <tr>

   <td width="402">Villa(const std::string &amp;property_name, int</td>

   <td width="271">area, Owner *owner, int</td>

  </tr>

  <tr>

   <td width="402">number_of_floors, bool having_garden);Apartment(const std::string &amp;property_name,</td>

   <td width="271">int area, Owner *owner, int</td>

  </tr>

  <tr>

   <td width="402">floor, bool having_elevator);Office(const std::string &amp;property_name, int having_wifi, bool having_reception);</td>

   <td width="271">area, Owner *owner, bool</td>

  </tr>

 </tbody>

</table>

Note-1: While creating instances of derived classes, you have to add that instances into property list of the owner as well if the owner is provided (not given as NULL pointer).

Note-2: A property can be owned by an owner. It can be bought or sold. If it changes hands, the owner information of this property should be updated.

There are 4 functions of these classes to be implemented:

<ul>

 <li>std::string get_name(): returns name of the property.</li>

 <li>void print_info(): prints name and area of the property and its owner in following format:</li>

</ul>

If has owner:

&lt;name of the property&gt; (&lt;area&gt; m2) Owner: &lt;name of the owner&gt; Else:

&lt;name of the property&gt; (&lt;area&gt; m2) Owner: No owner

<ul>

 <li>void set_owner(Owner *owner): takes an owner pointer and sets the property’s owner information.</li>

 <li>float valuate(): calculates and returns the value of the property. Each type of property has different valuation method:

  <ul>

   <li>Villa: <em>area </em>×10× <em>number</em>_<em>of</em>_<em>floors</em>. If it has garden double the value.</li>

   <li>Apartment: . If the building has elevator multiply the value by 1<em>.</em>5.</li>

   <li>Office: <em>area</em>×5. If there is a provided Wi-Fi, multiply the value by 1<em>.</em>3. If there is a provided reception service, multiply the value by 1<em>.</em>5. Multiply with both, if both of them are provided.</li>

  </ul></li>

</ul>

<h1>3             Examples</h1>

Example-Constructors

<table width="673">

 <tbody>

  <tr>

   <td width="673">int main(){Person per = Person(“Ahmet”, 5000, 35);Corporation corp = Corporation(“ACME”, 5000, “cankaya”);Villa est1 = Villa(“Villa 1”, 150, &amp;per, 2, false);Apartment est2 = Apartment(“Apartment 1”, 200, NULL, 7, true);per.print_info(); corp.print_info(); est1.print_info(); est2.print_info();return 0;}// Output—————————-Name: Ahmet Age: 35Name: ACME Address: cankayaVilla 1 (150 m2) Owner: AhmetApartment 1 (200 m2) Owner: No owner</td>

  </tr>

 </tbody>

</table>

Example-Buy/Sell Operations

<table width="673">

 <tbody>

  <tr>

   <td width="41">int</td>

   <td width="632">main()</td>

  </tr>

  <tr>

   <td width="41">{</td>

   <td width="632">Person per = Person(“Ahmet”, 50000, 45);Corporation corp = Corporation(“ACME”, 100000, “cankaya”);Villa est2 = Villa(“Villa 1”, 150, &amp;per, 2, false);Apartment est3 = Apartment(“Apartment 1”, 200, &amp;corp, 7, 1);Apartment est4 = Apartment(“Apartment 2”, 200, &amp;corp, 5, 0);cout &lt;&lt; “—————————-
”; per.list_properties(); corp.list_properties(); cout &lt;&lt; “—————————-
”; per.buy(&amp;est3, &amp;corp); cout &lt;&lt; “—————————-
”;</td>

  </tr>

 </tbody>

</table>




<table width="673">

 <tbody>

  <tr>

   <td width="673">per.list_properties(); corp.list_properties(); cout &lt;&lt; “—————————-
”; per.sell(&amp;est2, &amp;corp); cout &lt;&lt; “—————————-
”; per.list_properties(); corp.list_properties(); cout &lt;&lt; “—————————-
”;return 0;}// Output—————————Properties of Ahmet: Balance: 50000$1. Villa 1Properties of ACME: Balance: 100000$1.         Apartment 12.         Apartment 2—————————-[BUY] Property: Apartment 1 Value: 2100$ ACME—&gt;Ahmet—————————Properties of Ahmet: Balance: 47900$1.         Villa 12.         Apartment 1Properties of ACME: Balance: 102100$1. Apartment 2—————————-[SELL] Property: Villa 1 Value: 3000$ Ahmet—&gt;ACME—————————Properties of Ahmet: Balance: 50900$1. Apartment 1Properties of ACME: Balance: 99100$1.         Apartment 22.         Villa 1—————————-</td>

  </tr>

 </tbody>

</table>

Example-Balance Problem

<table width="673">

 <tbody>

  <tr>

   <td width="673">int main(){Person per = Person(“Ahmet”, 1000, 35);Corporation corp = Corporation(“ACME”, 1000, “cankaya”);Villa est1 = Villa(“Villa 1”, 150, &amp;per, 2, false);Apartment est2 = Apartment(“Apartment 1”, 200, &amp;corp, 7, 1);Apartment est3 = Apartment(“Apartment 2”, 200, &amp;corp, 5, 0);cout &lt;&lt; “—————————-
”; per.list_properties(); corp.list_properties(); cout &lt;&lt; “—————————-
”;// Ahmet cannot afford Apartment 1 per.buy(&amp;est2, &amp;corp);// Ahmet cannot afford Apartment 1 corp.sell(&amp;est2, &amp;per); cout &lt;&lt; “—————————-
”; per.list_properties(); corp.list_properties(); cout &lt;&lt; “—————————-
”;return 0;}// Output—————————Properties of Ahmet: Balance: 1000$1. Villa 1Properties of ACME:Balance: 1000$1.         Apartment 12.         Apartment 2—————————-[BUY] Property: Apartment 1 Value: 2100$ ACME—&gt;Ahmet[ERROR] Unaffordable property[SELL] Property: Apartment 1 Value: 2100$ ACME—&gt;Ahmet[ERROR] Unaffordable property—————————Properties of Ahmet: Balance: 1000$1. Villa 1Properties of ACME:Balance: 1000$1.         Apartment 12.         Apartment 2—————————-</td>

  </tr>

 </tbody>

</table>

Example-Selling not owned property or buying a property not owned by seller

<table width="673">

 <tbody>

  <tr>

   <td width="673">int main(){Person per = Person(“Ahmet”, 5000, 35);Corporation corp = Corporation(“ACME”, 5000, “cankaya”);Villa est1 = Villa(“Villa 1”, 150, &amp;per, 2, false);Apartment est2 = Apartment(“Apartment 1”, 200, &amp;corp, 7, 1);Apartment est3 = Apartment(“Apartment 2”, 200, &amp;corp, 5, 0);cout &lt;&lt; “—————————-
”; per.list_properties(); corp.list_properties(); cout &lt;&lt; “—————————-
”;// ACME do not own Villa 1 per.buy(&amp;est1, &amp;corp);// ACME do not own Villa 1 corp.sell(&amp;est1, &amp;per); cout &lt;&lt; “—————————-
”; per.list_properties(); corp.list_properties(); cout &lt;&lt; “—————————-
”;return 0;}// Output—————————Properties of Ahmet: Balance: 5000$1. Villa 1Properties of ACME:Balance: 5000$1.         Apartment 12.         Apartment 2—————————-[BUY] Property: Villa 1 Value: 3000$ ACME—&gt;Ahmet[ERROR] Transaction on unowned property[SELL] Property: Villa 1 Value: 3000$ ACME—&gt;Ahmet[ERROR] Transaction on unowned property—————————Properties of Ahmet: Balance: 5000$1. Villa 1Properties of ACME:Balance: 5000$1.         Apartment 12.         Apartment 2—————————-</td>

  </tr>

 </tbody>

</table>