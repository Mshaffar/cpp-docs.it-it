---
title: complex&lt;double&gt;
ms.date: 11/04/2016
f1_keywords:
- complex/std::complex<double>
helpviewer_keywords:
- complex<double> function
ms.assetid: 0d0b9d2a-9b9b-410b-82a0-86b6df127e47
ms.openlocfilehash: 8955669f4bc6fd7b3b373751e0e5134205dd1657
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689784"
---
# <a name="complexltdoublegt"></a>complex&lt;double&gt;

Descrive un oggetto che archivia una coppia ordinata di oggetti, entrambi di tipo **Double**, il primo rappresenta la parte reale di un numero complesso e il secondo rappresenta la parte immaginaria.

## <a name="syntax"></a>Sintassi

```cpp
template <>
class complex<double> {
public:
    constexpr complex(
    double RealVal = 0,
    double ImagVal = 0);

constexpr complex(const complex<double>& complexNum);

constexpr explicit complex(const complex<long double>& complexNum);
// rest same as class template complex
};
```

### <a name="parameters"></a>Parametri

*Realval* \
Valore di tipo **double** per la parte reale del numero complesso che viene costruito.

@No__t_1 *ImagVal*
Valore di tipo **double** per la parte immaginaria del numero complesso che viene costruito.

\ *complexNum*
Numero complesso di tipo **float** o di tipo **long double** le cui parti reale e immaginaria vengono usate per inizializzare un numero complesso di tipo **Double** da costruire.

## <a name="return-value"></a>Valore restituito

Numero complesso di tipo **double**.

## <a name="remarks"></a>Note

La specializzazione esplicita del modello di classe Complex a una classe complessa di tipo **Double** differisce dal modello di classe solo nei costruttori che definisce. La conversione da **float** a **Double** può essere implicita, ma la conversione da **long double** a **Double** deve essere **esplicita**. L'uso di una conversione **esplicita** esclude l'inizializzazione con conversione del tipo tramite la sintassi di assegnazione.

Per ulteriori informazioni sul modello di classe `complex`, vedere [classe Complex](../standard-library/complex-class.md). Per un elenco di membri del modello di classe `complex`, vedere.

## <a name="example"></a>Esempio

```cpp
// complex_comp_dbl.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // The first constructor specifies real & imaginary parts
   complex <double> c1 ( 4.0 , 5.0 );
   cout << "Specifying initial real & imaginary parts,\n"
        << "as type double gives c1 = " << c1 << endl;

   // The second constructor initializes values of the real &
   // imaginary parts using those of complex number of type float
   complex <float> c2float ( 4.0 , 5.0 );
   complex <double> c2double ( c2float );
   cout << "Implicit conversion from type float to type double,"
        << endl << "gives c2double = " << c2double << endl;

   // The third constructor initializes values of the real &
   // imaginary parts using those of a complex number
   // of type long double
   complex <long double> c3longdouble ( 4.0 , 5.0 );
   complex <double> c3double ( c3longdouble );
   cout << "Explicit conversion from type float to type double,"
        << endl << "gives c3longdouble = " << c3longdouble << endl;

   // The modulus and argument of a complex number can be recovered
   double absc3 = abs ( c3longdouble );
   double argc3 = arg ( c3longdouble );
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "
        << absc3 << endl;
   cout << "Argument of c3 is recovered from c3 using:" << endl
        << "arg ( c3 ) = " << argc3 << " radians, which is "
        << argc3 * 180 / pi << " degrees." << endl;
}
/* Output:
Specifying initial real & imaginary parts,
as type double gives c1 = (4,5)
Implicit conversion from type float to type double,
gives c2double = (4,5)
Explicit conversion from type float to type double,
gives c3longdouble = (4,5)
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 6.40312
Argument of c3 is recovered from c3 using:
arg ( c3 ) = 0.896055 radians, which is 51.3402 degrees.
*/
```

## <a name="requirements"></a>Requisiti

**Intestazione**: \<complex>

**Spazio dei nomi:** std

## <a name="see-also"></a>Vedere anche

[Classe complex](../standard-library/complex-class.md)\
[Thread Safety nella libreria standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
