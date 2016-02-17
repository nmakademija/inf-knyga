Informatikos olimpiados: algoritmai ir taikymo pavyzdžiai
=========================================================

Įvadas
------

  | *Čia reikia bėgti kiek įkabini, kad išsilaikytum toje pačioje vietoje.*
  | *O jei nori patekti kur nors kitur, reikia bėgti dvigubai greičiau.*

  Luisas Kerolis, „Alisa veidrodžių karalystėje“

Ši knygelė skirta moksleiviams, kurie ruošiasi dalyvauti informatikos
olimpiadose. Galima svarstyti ir ginčytis, ką reiškia žodis
*informatika*, tačiau pasaulinių olimpiadų kontekste informatikos
olimpiada – tai pirmiausia įdomūs algoritmavimo uždaviniai, kuriems
išspręsti reikia ne tik išmanyti įvairius algoritmus, bet ir rasti
įdomių, netradicinių sprendimų bei sugebėti per keletą valandų
„materializuoti“ savo idėjas veikiančiomis programomis.

Informatikos olimpiados jau beveik dvidešimt metų kasmet rengiamos
Lietuvoje ir beveik tiek pat metų geriausi Nacionalinės informatikos
olimpiados dalyviai atstovauja Lietuvai Baltijos bei pasaulinėse
informatikos olimpiadose. Knygelėje aprašyti svarbūs algoritmai ir
metodai, kuriuos turėtų žinoti kiekvienas norintis sėkmingai dalyvauti
šiose olimpiadose. Tiesa, čia nėra griežtų algoritmų teisingumo įrodymų,
kurie pateikiami aukštųjų mokyklų vadovėliuose. Algoritmų teisingumas
dažniausiai grindžiamas intuityviai, o teorija iliustruojama konkrečiais
uždaviniais, paimtais iš realių olimpiadų. Leidinyje pateikėme
sutrumpintas uždavinių sąlygas, atmetę daug detalių, susijusių su
automatiniu programų testavimu. Dauguma sprendimų pateikti kaip Paskalio
kalbos [#f1]_ procedūros ar funkcijos, stengiantis kuo mažiau
prisirišti prie konkrečios programavimo kalbos subtilumų. Tad leidinys
puikiausiai tiks ir programuojantiems kitomis programavimo kalbomis.

Tikimės, kad knygelė bus pirmasis rengimosi informatikos olimpiadoms
etapas. Jį įveikus dar bus ilgas kelias, kuriame teks spręsti daugybę
įdomių uždavinių ir kuriuo reikės bėgti dvigubai greičiau, norint
pasiekti daugiau.

Už vertingas pastabas ir pagalbą rengiant šį leidinį nuoširdžiai
dėkojame Lietuvos moksleivių informatikos olimpiados vertinimo komisijos
nariams Justui Kranauskui, Martynui Kriaučiūnui bei Mindaugui Plukui.

Autoriai

Turinys
-------

.. toctree::
  :maxdepth: 2

  01_algoritmas
  02_euklido
  03_pirminiai
  04_rekursija

  05_perrinkimas
  06_rikiavimas
  07_grafų_pagrindai
  08_oilerio_ciklai

  09_orientuoti_grafai
  10_dijkstra
  11_medžiai

  12_dinaminis
  13_žaidimai

  literatūra
  LICENSE

.. rubric:: Išnašos

.. [#f1]
  Knygelėje pateiktos programos kompiliuotos Free Pascal
  kompiliatoriumi, kuris naudojamas ir tarptautinėse olimpiadose
  (`www.freepascal.org <http://www.freepascal.org>`_).

..
  Pandoc:
  pandoc +RTS -K64777216 -RTS -f html -t rst -o leidinys2.rst leidinys2.html

..
  VIM Sed:
    :%s/\.\. |image\(.\)| image:: data:image\/jpeg;base64,/.. |image\1| image:: images\/leidinys3\/\1\.jpg\r/g
    :%s/\.\. |image\(.\)| image:: data:image\/png;base64,/.. |image\1| image:: images\/leidinys3\/\1\.png\r/g
    :%s/\.\. |image\(..\)| image:: data:image\/png;base64,/.. |image\1| image:: images\/leidinys3\/\1\.png\r/g
    :%s/\.\. |image\(.\)| image:: //g
    :%s/\.\. |image\(..\)| image:: //g

..
  Python:
  with open('images_base64', 'rb') as fp:
      data = fp.read()
      lines = data.splitlines()
      imgs = [
          (path, data)
          for path, data in zip(lines[0::2], lines[1::2])
          ]
      for path, data in imgs:
          open(path, 'wb').write(data.decode('base64'))
