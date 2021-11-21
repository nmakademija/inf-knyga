==============================================================================
Pirmasis algoritmas – Euklido algoritmas didžiausiam bendrajam dalikliui rasti
==============================================================================

  | *Kartą mokinys, išmokęs savo pirmąją geometrijos teoremą,*
  | *paklausė Euklido: „Kokia man nauda, kad šitai išmoksiu?“.*
  | *Euklidas pakvietė savo vergą ir tarė: „Duok šiam žmogui*
  | *drachmą, nes jis turi turėti naudos iš to, ką išmoksta.“*
  | J. Stobijus (Joannes Stobaeus), V a. pr. Kr.

.. figure:: images/vieši/Euklid.jpg
  :align: center
  :width: 200px
  :alt: Euklido portretas

  Euklido portretas

Šiame skyrelyje susipažinsime su seniausiu netrivialiu algoritmu,
išlikusiu iki šių dienų. Tai algoritmas didžiausiam bendrajam
dalikliui rasti. Nėra žinoma, kas šį algoritmą sugalvojo (ir ar tai
buvo vienas žmogus). Dar prieš Euklidui (graikų k.
Εὐκλείδης, *Eukleides*) aprašant šį algoritmą, jį savo
veikale cituoja Aristotelis. Euklidas algoritmą kruopščiai aprašė
garsiajame veikale *„Pradmenys“* (apie 300 m. pr. Kr.), todėl
algoritmui ir prigijo Euklido vardas.

Didžiausias bendrasis daliklis ir mažiausias bendrasis kartotinis
=================================================================

Prisiminkime *didžiausio bendrojo daliklio* (DBD) ir *mažiausio
bendrojo kartotinio* (MBK) sąvokas.

Sakome, kad **skaičius** :math:`\mathbf{a}` **dalija skaičių**
:math:`\mathbf{b}`, jei egzistuoja toks sveikasis skaičius :math:`k`,
kad :math:`b = ka;` žymime :math:`a | b`.

Pavyzdžiui, :math:`5|30`, nes :math:`30 = 6 \cdot 5`. Skaičius 1
dalija visus skaičius (:math:`1|a`, visiems sveikiesiems :math:`a`), o
skaičių 0 dalija visi skaičiai, išskyrus patį 0 (:math:`a|0`,
visiems sveikiesiems :math:`a`, :math:`a\neq0`).

Dviejų neneigiamų skaičių :math:`a` ir :math:`b` **didžiausiu
bendruoju dalikliu** (DBD) vadinamas didžiausias skaičius, dalijantis
:math:`a` ir :math:`b`. Pavyzdžiui, :math:`DBD(12, 8) = 4`,
:math:`DBD(3, 6) = 3`, :math:`DBD(7, 9) = 1`.

Neneigiamų skaičių :math:`a` ir :math:`b` **mažiausiu bendruoju
kartotiniu** (MBK) vadinamas mažiausias teigiamas skaičius, kurį
dalija :math:`a` ir :math:`b`. Pavyzdžiui, :math:`MBK(12, 8) = 24`,
:math:`MBK(3, 6) = 6`, :math:`MBK(7, 9) = 63`.

Natūralus būdas rasti :math:`DBD(a, b)` – išskaidyti skaičius
:math:`a` ir :math:`b` pirminiais daugikliais ir išrinkti visus
*bendruosius* šių skaičių pirminius daugiklius. Pavyzdžiui,
:math:`12 = \mathbf{2 \cdot 2} \cdot 3`,
:math:`8 = \mathbf{2 \cdot 2} \cdot 2`, bendrieji
daugikliai yra :math:`\mathbf{2 \cdot 2}`, taigi
:math:`DBD(12, 8) = 4`. Šiuo būdu tarsi konstruojame :math:`DBD`,
stengdamiesi jį padaryti kuo didesnį (rinkdami kuo daugiau skaičiaus
:math:`a` pirminių daugiklių), tačiau žiūrėdami, kad :math:`DBD`
dalytų ir skaičių :math:`b`.

:math:`MBK(a, b)` taip pat galime rasti išskaidę skaičius :math:`a`
ir :math:`b` į pirminius daugiklius. Kadangi :math:`a|MBK(a, b)`, tai
:math:`MBK` turi priklausyti visi :math:`a` pirminiai daugikliai.
Tačiau ir :math:`b|MBK(a, b)`, todėl pridedame skaičiaus :math:`b`
pirminius daugiklius, kurių trūksta (būtent, daugiklius, kurie *nėra
bendrieji* skaičiams :math:`a` ir :math:`b`). Pavyzdžiui,
:math:`MBK(12, 8) = 2 \cdot 2 \cdot 3 \cdot 2 = 24`.

Šie :math:`DBD` ir :math:`MBK` konstravimo būdai paaiškina ir šiuos
skaičius siejančią lygybę: :math:`DBD(a, b) \cdot MBK(a, b) = a \cdot b`.

Euklido algoritmas
==================

| *An algorithm must be seen to be believed.*
| *Algoritmą reikia pamatyti, kad juo patikėtum.*
| Donaldas Knutas (Donald Knuth)

Tarkime, reikia rasti skaičių :math:`a` ir :math:`b` didžiausiąjį
bendrą daliklį. Atliekame tokius veiksmus:

-  jei :math:`b = 0`, tai :math:`DBD(a, b)` lygus :math:`a`,
   priešingu atveju :math:`a_{2} = b`, :math:`b_{2} = a mod b`
   (lygus liekanai, gautai padalijus :math:`a` iš :math:`b`)

-  jei :math:`b_{2} = 0`, tai :math:`DBD(a, b)` lygus :math:`a_{2}`,
   priešingu atveju :math:`a_{3} = b_{2}`,
   :math:`b_{3} = a_{2} mod b_{2}`

-  …

-  jei :math:`b_k = 0`, tai :math:`DBD(a, b)` lygus :math:`a_k`,
   priešingu atveju :math:`a_{k+1} = b_{k}`,
   :math:`b_{k+1} = a_{k} mod b_{k}`.

Kadangi dalydami iš skaičiaus :math:`n` galime gauti liekaną nuo 0
iki :math:`n-1`, tai
:math:`b > b_{2} > \cdots > b_{k} > \cdots > b_{n} = 0`,
ir algoritmas atliks baigtinį skaičių veiksmų (anksčiau ar vėliau
:math:`b_{i}` taps lygus 0, tad algoritmas baigs darbą).

Raskime skaičių :math:`a = 12` ir :math:`b = 8` :math:`DBD`
naudodamiesi Euklido algoritmu:

-  :math:`b > 0`, taigi skaičiuojame :math:`a_{2} = b = 8`,
   :math:`b_{2} = a mod b = 12 mod 8 = 4`.

-  :math:`b_{2} > 0`, taigi skaičiuojame
   :math:`a_{3} = b_{2} = 4`,
   :math:`b_{3} = a_{2} mod b_{2} = 8 mod 4 = 0`.

-  :math:`b_{3} = 0`, taigi :math:`DBD(a, b) = a_{3} = 4`.

Gavome :math:`DBD(12, 8) = 4`. Užrašysime Euklido algoritmą Paskalio ir C++ kalbomis.

.. tabs::

  .. tab:: Paskalis

    .. code-block:: unicode_pascal

      function DBD(a, b : longint) : longint;
        var c : longint;
      begin
        while b > 0 do begin
          c := a;
          a := b;
          b := c mod b;
        end;
        DBD := a;
      end;

  .. tab:: C++

    .. code-block:: cpp

      long long DBD(long long a, long long b) {
          long long c;
          while (b > 0) {
              c = a;
              a = b;
              b = c % b;
          }
          return a;
      }

Jei reikia rasti dviejų skaičių DBD, tačiau nežinome, ar jie
teigiami, funkciją iškviečiame perduodami skaičių modulius:
``DBD(abs(a), abs(b))``.

Euklido algoritmas yra **teisingas**, nes remiasi sąryšiu:
:math:`DBD(a, b) = DBD(b, a mod b)`. Šio sąryšio teisingumu
nesunku įsitikinti pasinaudojus lygybe:

.. math::

  a = (a div b) \cdot b + a mod b.

Du skaičiai turi vieną ir tik vieną didžiausiąjį bendrą daliklį.
Tarkime, :math:`DBD(a, b) = d`. Daliklis :math:`d` dalija skaičių
:math:`a` ir taip pat dalija jo dalį :math:`(a div b) \cdot b`,
todėl turi dalyti ir likusią skaičiaus :math:`a` dalį –
:math:`a mod b`. Taigi skaičių :math:`a` ir :math:`b` didžiausias
bendrasis daliklis yra ir (mažesnių) skaičių poros :math:`b` ir
:math:`a mod b` didžiausias bendrasis daliklis, t. y.
:math:`DBD(a, b) = d = DBD(b, a mod b)`.

Pamėginkime įvertinti Euklido algoritmo **sudėtingumą**. Pasiremsime
nelygybe :math:`n mod m < n/2`, kur :math:`n` ir :math:`m` –
sveikieji neneigiami skaičiai ir :math:`n \geq m`.

Nelygybė teisinga, nes:

-  jei :math:`m \leq n/2`, tuomet :math:`n mod m < m \leq n/2`;

-  jei :math:`m > n/2`, tuomet :math:`n div m = 1`; tada lygybę
   :math:`n = (n div m) m + n mod m` perrašome:
   :math:`n = m + n mod m`; gauname
   :math:`n mod m = n - m < n - n/2 = n/2`.

Tarkime, kad :math:`a > b` (jei taip nėra, tai atliekant ciklą
pirmąjį kartą, šie skaičiai bus sukeisti vietomis). Ciklo viduje
atliekamas operacijas galime laikyti elementariomis, tad Euklido
algoritmo sudėtingumas tiesiog proporcingas tam, kiek kartų bus
atliekamas ciklas while.

Panagrinėkime, kaip keičiasi kintamųjų :math:`a` ir :math:`b`
reikšmės vykdant while ciklą. Sakykime, pradinės šių kintamųjų
reikšmės yra :math:`a_0` ir :math:`b_0`. Po pirmos ciklo iteracijos
:math:`a_1 = b_0`, o :math:`b_1 = a_0 mod b_0 < a_0/2`. Po
antros iteracijos :math:`a_2 = b_1 < a_0/2`, o
:math:`b_2 = a_1 mod b_1 < a_2`. Gavome, kad atlikus dvi ciklo
iteracijas, pirmojo kintamojo reikšmė sumažėja daugiau negu dvigubai
ir dar vis galioja :math:`a \geq b`. Po keturių iteracijų pirmojo
kintamojo reikšmė bus daugiau nei keturis kartus mažesnė už
pradinę ir t. t. Taigi matyti, kad ciklas bus vykdomas ne daugiau kaip
:math:`2 \log{a}` kartų. Dabar jau nesunku įvertinti, kad Euklido
algoritmo sudėtingumas yra :math:`O(\log{a})`.

Kadangi Euklido algoritmas apibrėžiamas rekurentiniais sąryšiais:

  | :math:`DBD(a, b) = a`, jei :math:`b = 0`
  | :math:`DBD(a, b) = DBD(b, a mod b)`, jei :math:`b > 0`

tai Euklido algoritmą nesunku užrašyti rekursyvia [#f7]_ funkcija:

.. tabs::

  .. tab:: Paskalis

    .. code-block:: unicode_pascal

      function DBD(a, b : longint) : longint;
      begin
        if b = 0 then
          DBD := a
        else
          DBD := DBD(b, a mod b);
      end;

  .. tab:: C++

    .. code-block:: cpp

      long long DBD(long long a, long long b) {
          return b == 0 ? a : DBD(b, a%b);
      }

Pastebėkime, kad jei :math:`a < b`, algoritmas pirmu žingsniu šiuos
skaičius sukeičia vietomis, pavyzdžiui,
:math:`DBD(24, 54) = DBD(54, 24) = DBD(24, 6) = DBD(6, 0) = 6`.

Beje, pats Euklidas šį algoritmą aprašė kiek kitaip. Mat graikų
matematikai nelaikė, kad vienetas dalija kitą teigiamą skaičių.
Buvo galimi trys variantai: arba du teigiami sveikieji skaičiai yra abu
lygūs vienetui, arba tarpusavyje pirminiai, arba turi bendrą
didžiausią daliklį. Vienetas netgi nebuvo laikomas skaičiumi, o
nulis apskritai neegzistavo.

Euklido algoritmo taikymas, mažiausio bendrojo kartotinio (MBK) radimas
=======================================================================

Didžiausiojo bendrojo daliklio gali prireikti sprendžiant įvairius
skaičiavimo uždavinius. Vienas iš pavyzdžių – prastinant trupmenas,
skaitiklį ir vardiklį reikia padalyti iš didžiausio jų bendrojo
daliklio.

Euklido algoritmas leidžia efektyviai apskaičiuoti ir mažiausią
bendrąjį kartotinį:

.. tabs::

  .. tab:: Paskalis

    .. code-block:: unicode_pascal

      function MBK(a, b : longint) : longint;
      begin
        MBK := a * b div DBD(a, b);
      end;

  .. tab:: C++

    .. code-block:: cpp

      long long MBK(long long a, long long b) {
          return a / DBD(a,b) * b;
      }

.. note::

  Svarbu nepamiršti, kad ``longint`` tipo kintamieji gali saugoti
  reikšmes, ne didesnes negu :math:`2^{31} - 1`. Taigi :math:`MBK` bus
  skaičiuojamas teisingai tik tuo atveju, kai skaičius :math:`a` ir
  :math:`b` sandauga neviršija šio skaičiaus.

Naudodamiesi Euklido algoritmu galime rasti ne tik dviejų, bet ir
keleto skaičių :math:`DBD` bei :math:`MBK`. Kadangi
:math:`DBD(a, b, c) = DBD(DBD(a, b), c)`, ir
:math:`MBK(a, b, c) = MBK(MBK(a, b), c)`. Šias lygybes suprasti
ir įrodyti nesunku įsivaizduojant, kaip konstruotume :math:`DBD` ir
:math:`MBK` iš skaičių :math:`a`, :math:`b` ir :math:`c` pirminių
daugiklių.

Tarkime, masyve :math:`m` yra :math:`k` sveikųjų skaičių. Pateiksime
fragmentą, randantį visų :math:`k` skaičių :math:`DBD` ir
:math:`MBK`:

.. tabs::

  .. tab:: Paskalis

    .. code-block:: unicode_pascal

      visųDBD := 0; { po pirmo žingsnio taps lygiu m[1] }
      for i := 1 to k do
        visųDBD := DBD(abs(m[i]), visųDBD);

  .. tab:: C++

    .. code-block:: cpp

      int visųDBD = 0; // po pirmo žingsnio taps lygiu m[0]
      for(int i = 0; i < n; i++) {
          visųDBD = DBD(visųDBD, abs(m[i]));
      }

.. tabs::

  .. tab:: Paskalis

    .. code-block:: unicode_pascal

      visųMBK := 1; { po pirmo žingsnio taps lygiu m[1] }
      for i := 1 to k do
        visųMBK := MBK(abs(m[i]), visųMBK);

  .. tab:: C++

    .. code-block:: cpp

      int visųMBK = 1; // po pirmo žingsnio taps lygiu m[0]
      for(int i = 0; i < n; i++) {
          visųMBK = MBK(visųMBK, abs(m[i]));
      }

.. rubric:: Išnašos

.. [#f7]
  Su rekursija išsamiai susipažinsime :ref:`skyrius-rekursija`
  skyriuje.
