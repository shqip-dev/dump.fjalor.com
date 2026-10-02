# Fjalori i ASHSH-së, i strukturuar

Ky depo mban të dhënat e «Fjalorit të gjuhës së sotme shqipe» (Akademia e Shkencave e
Shqipërisë, 2006) në dy trajta:

| Skedari | Çfarë është |
|---|---|
| `ashash-original.json` | Teksti i fjalorit ashtu siç u mblodh: 31.366 zëra, secili një titull dhe një tekst i pandarë me shënimet e fjalorit (shkurtime, mbaresa, shenja). |
| `ashash.json` | **I njëjti fjalor, i strukturuar**: 45.586 fjalë, secila me fushat e veta (gramatika, kuptimet, shembujt, shprehjet, lidhjet me fjalë të tjera). |

`ashash.json` është përmbajtja që shfaqet në [fjalor.com](https://fjalor.com), e shkarkuar
më 2 tetor 2026. Asgjë nuk i është shtuar tekstit të Akademisë: struktura vetëm e
riorganizon atë që thotë origjinali. Çdo fjalë mban te fusha `source` vendin e saj në
origjinal, që të mund të krahasohet.

## Nga origjinali te struktura

Një zë i origjinalit:

```json
{
  "word": "abdik{/}oj",
  "definitions": [
    "<span>jokal.</span>, -ova, -uar <span>libr.</span> heq dorë nga pushteti mbretëror. • abdikim,-i <span>m.</span> <span>sh.</span> -e(t) veprimi sipas foljes."
  ]
}
```

Në `ashash.json` ky zë bëhet dy fjalë: folja dhe emri që në origjinal vjen pas shenjës `•`.

```json
{
  "id": "5d473e7e-f49c-5348-92bf-e64da879158f",
  "lemma": "abdikoj",
  "pos": "fol",
  "source": "abdikoj",
  "grammar": {
    "Verb": {
      "aorist": "abdikova",
      "participle": "abdikuar",
      "transitivity": "jokal"
    }
  },
  "senses": [
    {
      "definition": "heq dorë nga pushteti mbretëror",
      "labels": {
        "register": [
          "libr"
        ]
      }
    }
  ]
}
```

```json
{
  "id": "133e42ce-ea6b-53f9-8ade-160b0a051490",
  "lemma": "abdikim",
  "pos": "em",
  "source": "abdikoj • abdikim",
  "grammar": {
    "Noun": {
      "definite": "abdikimi",
      "gender": "m",
      "plurals": [
        {
          "indefinite": "abdikime",
          "definite": "abdikimet"
        }
      ]
    }
  },
  "family": {
    "id": "5d473e7e-f49c-5348-92bf-e64da879158f",
    "lemma": "abdikoj"
  },
  "senses": [
    {
      "definition": "veprimi sipas foljes [[abdikoj]]"
    }
  ]
}
```

Mbaresat e shkurtuara (`-ova, -uar`, `-i`, `-e(t)`) janë shkruar të plota (`abdikova`,
`abdikuar`, `abdikimi`, `abdikime`, `abdikimet`), shkurtimet (`jokal.`, `libr.`, `m.`) janë
bërë fusha me kode, dhe emri i prejardhur lidhet me foljen përmes `family`.

### Si lexohet origjinali

Shënimet e origjinalit ndjekin rregullat që Akademia i shpjegon te «Shpjegime për ndërtimin
dhe përdorimin e fjalorit» ([fjalori.online/parathenie](https://fjalori.online/parathenie)).
Ato shpjegime janë shkruar për «Fjalorin e madh të gjuhës shqipe» (2025), por ndërtimi i
zërit është i njëjtë; ndryshojnë vetëm disa shenja. Shkurt:

- **Zëri** ka tri pjesë: fjala në trajtën përfaqësuese me trajtat plotësuese (trajta e
  shquar dhe shumësi për emrat, femërorja për mbiemrat, e kryera e thjeshtë dhe pjesorja
  për foljet); shpjegimet e kuptimeve, secili me shembujt e vet; në fund frazeologjia.
- **Viza e pjerrët** ndan pjesën e pandryshueshme të fjalës nga pjesa që ndryshon:
  `abdik/oj, -ova, -uar` lexohet *abdikoj, abdikova, abdikuar*. Në këtë origjinal ajo
  shkruhet `{/}`, mbaresa e trajtës së shquar vjen brenda titullit (`agjent{,-i}`), dhe
  mbaresat e tjera fillojnë me vizë. Trajtat krejt të parregullta jepen të plota.
- **Kuptimet** numërohen `1.`, `2.`, `3.`. Brenda një kuptimi, pikëpresja ndan nënkuptime
  ose shpjegime të afërta, dhe dy pikat hapin shembujt.
- **Shenja `•`** hap, brenda të njëjtit zë, një fjalë të prejardhur nga titulli (emri i
  veprimit, trajta vetvetore a pësore e foljes, mbiemri, ndajfolja).
- **Shenja `★`** hap frazeologjinë: çdo shprehje pasohet nga shpjegimi i saj.
- **Numrat romakë** pas titullit (`bie I`, `bie II`) dallojnë homonimet.
- **Shkurtimet** janë katër llojesh: për pjesët e ligjëratës dhe kategoritë gramatikore
  (`m.`, `f.`, `sh.`, `kal.`, `jokal.`, `vetv.`, `ndajf.`); për llojet dhe kufizimet e
  kuptimeve (`fig.`, `përmb.`, `kryes.`); për ligjërimin dhe fushën e përdorimit (`bised.`,
  `libr.`, `vjet.`, `bot.`, `zool.`, `fet.`); për ngjyrimin emocional (`përk.`, `tall.`,
  `përb.`, `keq.`). Kur vlejnë disa njëherësh, shkruhen njëri pas tjetrit. `spec.` shënon
  një term që përdoret në disa fusha, `fj. u.` një fjalë të urtë.
- Disa zëra kanë edhe fushën `attributes`, p.sh. `"lexo": "abdes-hanë"`: si lexohet një
  fjalë ku dy shkronja fqinje nuk janë dyshkronjësh.

## Si u ndërtua

1. Një program e ndau çdo zë të origjinalit në fjalë, kuptime, shembuj, shprehje dhe
   etiketa, dhe i shkroi të plota trajtat e shkurtuara.
2. Një rishikim automatik e krahasoi çdo fjalë me tekstin e origjinalit: asnjë fjalë e
   origjinalit nuk duhet të humbasë dhe asnjë nuk duhet të shtohet.
3. Rreth 1.100 zëra që rishikimi automatik nuk i kaloi u panë një nga një dhe u ndreqën
   me dorë.

Origjinali nuk i ndjek gjithmonë rregullat e veta, prandaj shpjegimet e Akademisë u
përdorën si udhëzues dhe jo si ligj: ku shënimi ishte i paqartë, vendosi teksti.

### Çfarë kemi vendosur vetë

Këto zgjedhje nuk i thotë origjinali; janë mënyra si e kemi kthyer në strukturë:

- **Çdo fjalë pas `•` është fjalë më vete**, me kuptimet e veta, dhe te `family` mban
  fjalën kryesore të zërit. Kështu 31.366 zëra bëhen 45.586 fjalë.
- **Trajtat shkruhen të plota**, kurrë si mbaresë: `bjeshka`, jo `-a`.
- **Një zë me disa pjesë ligjërate ndahet**: kur një kuptim i numëruar ka gramatikë të
  vetën (p.sh. mbiemri që përdoret edhe si emër me trajta të tjera), ai bëhet fjalë më vete.
- **Një etiketë pas pikëpresjes hap një nënkuptim**: «…; *fig.* *libr.* …» bëhet
  `subsenses`, me etiketat dhe shembujt e vet.
- **Shumësi i dhënë brenda një kuptimi** («2. edhe sh. -ra(t)») shkon te shumësat e emrit,
  me shënimin «në kuptimin 2».
- **Një `sh.` pa mbaresë** nuk thotë asgjë që mund të ruhet, prandaj nuk ruhet: as etiketë,
  as shumës i shpikur.
- **«si em. m.», «edhe si em. f.», «mb. f.»** janë etiketa gramatikore (`si.em.m`,
  `edhe.si.em.f`, `f`), jo tekst brenda përkufizimit.
- **«si mallk.», «edhe ur.»** te një kuptim janë ngjyrim (`mallk`, `ur`, `betim`); pas një
  shembulli a një shprehjeje janë lloji i tij (`kind`).
- **Trajta vetvetore dhe pësore**: kur kanë të njëjtën trajtë («• afrohem vetv. … / pës.»)
  janë një fjalë, me diatezë `vetv` dhe etiketën `pës`; kur trajta ndryshon, pësorja është
  fjalë më vete. Te kuptimi lidhen me foljen veprore përmes një lidhjeje `jovepr`.
- **Një titull në kllapa «(x)»** është variant i titullit para tij dhe shkon te `spellings`
  e asaj fjale.
- **Termat me shpjegim mes shembujve** (pa `★`) janë shembuj me `gloss`, jo shprehje.
- **Referimet** si «veprimi sipas foljes» janë kthyer në lidhje: `[[abdikoj]]` në tekst.
- **Gabimet e dukshme të shtypit** janë ndrequr (p.sh. një titull i shkruar gabim në
  origjinal), kurse drejtshkrimi dhe fjalët e tekstit nuk janë prekur.

## Formati

`ashash.json` është një listë JSON me 45.586 objekte, një fjalë për rresht, në rendin e
alfabetit shqip (`c` para `ç`, `d` para `dh`, e kështu me radhë). Një fushë që mungon ka
vlerën e saj të zakonshme: bosh, ose kodi i parë i tabelës përkatëse.

### Fjala

| Fusha | Çfarë mban |
|---|---|
| `id` | Identifikuesi i fjalës (UUID). Lidhjet mes fjalëve e përdorin këtë. |
| `lemma` | Fjala në trajtën përfaqësuese, pa nyje dhe pa shënime. |
| `homonym` | Numri i homonimit (`1` për «bie I»), vetëm kur origjinali e numëron. |
| `pos` | Pjesa e ligjëratës, si kod (shih [Kodet](#kodet)). |
| `source` | Vendi në origjinal: titulli i zërit («bie I»), dhe për fjalët pas `•` edhe vetë fjala («abdikoj • abdikim»). |
| `grammar` | Gramatika, sipas pjesës së ligjëratës (më poshtë). |
| `labels` | Etiketat që vlejnë për gjithë fjalën (më poshtë). |
| `forms` | Trajta të veçanta që origjinali i jep shprehimisht: `form`, `features` (kode), `note`. |
| `family` | Fjala kryesore e familjes: `id`, `lemma`, `homonym`. |
| `pronunciations` | Shqiptimi. Sot vetëm `respelling`: fjala me vizë aty ku dy shkronja lexohen veç («akt-hetim»). |
| `spellings` | Trajta të tjera të shkruara të fjalës: `form`, `note`. |
| `senses` | Kuptimet, me radhë. |
| `phrases` | Shprehjet frazeologjike (pas `★` në origjinal). |
| `relations` | Lidhjet me fjalë të tjera që vlejnë për gjithë fjalën. |
| `notes` | Shënime të origjinalit që nuk i përkasin një kuptimi: `kind`, `text`. |

### Gramatika (`grammar`)

Një objekt me një çelës të vetëm, që thotë llojin:

| Çelësi | Fushat |
|---|---|
| `Noun` (emër) | `gender` gjinia; `definite` trajta e shquar njëjës; `plurals` shumësat, secili me `indefinite`, `definite` dhe ndonjëherë `note`; `number` kur përdoret vetëm në një numër; `article` nyja e përparme; `indeclinable` |
| `Adjective` (mbiemër) | `article` nyja; `feminine` femërorja njëjës; `plural_masculine`, `plural_feminine` |
| `Verb` (folje) | `aorist` e kryera e thjeshtë; `participle` pjesorja; `transitivity`; `voice` diateza; `third_person_only`; `impersonal` |
| `Pronoun`, `Numeral`, `Affix` | `kind` lloji |

### Kuptimi (`senses`)

| Fusha | Çfarë mban |
|---|---|
| `definition` | Shpjegimi. |
| `construction` | Ndërtimi me të cilin përdoret fjala në këtë kuptim. |
| `labels` | Etiketat e kuptimit. |
| `examples` | Shembujt: `text`; `gloss` shpjegimi i shembullit; `kind` lloji (fjalë e urtë, urim, mallkim, betim); `labels`. |
| `relations` | Lidhjet e këtij kuptimi me fjalë të tjera. |
| `subsenses` | Nënkuptimet: po këto fusha, një nivel më thellë. |

Kuptimet numërohen sipas vendit: i pari është `1`, nënkuptimi i parë i të dytit është `2a`.

### Shprehja (`phrases`)

`text` është shprehja; `kind` lloji kur nuk është frazeologjike; `labels` etiketat;
`senses` kuptimet e saj, me të njëjtat fusha si kuptimet e fjalës.

### Lidhja (`relations`)

`kind` thotë llojin e lidhjes (sinonim, antonim, femërorja e, trajta joveprore e…) dhe
`target` fjalën tjetër: `id`, `lemma`, `homonym`, dhe `senses` kur lidhja është me kuptime
të caktuara të saj (`["2"]`, `["1a"]`). Një `target` pa `id` është një fjalë që origjinali
e përmend, por që nuk është zë i fjalorit.

### Etiketat (`labels`)

| Fusha | Çfarë thotë |
|---|---|
| `register` | Ligjërimi: bisedor, libror, poetik… |
| `attitude` | Ngjyrimi: keqësues, ironik, përkëdhelës… |
| `domains` | Fusha e dijes: botanikë, mjekësi, ushtri… |
| `time` | Vendi në kohë: e vjetruar. |
| `usage` | Shpeshtësia: kryesisht, zakonisht, rrallë. |
| `grammar` | Kushte gramatikore të përdorimit: në shumës, pavetore, edhe si emër… |
| `figurative` | Kuptim i figurshëm, ose edhe i figurshëm. |
| `areas` | Ku përdoret: `dialects`. |

Të gjitha janë lista kodesh, përveç `figurative` që është një kod i vetëm.

### Teksti

Fushat me tekst (`definition`, `text`, `gloss`, `note`) përdorin një shënim të thjeshtë,
kurrë HTML:

- `*fjalë*` është shkrim i pjerrët, `**fjalë**` shkrim i trashë;
- `[[abdikoj]]` është lidhje te një fjalë; `[[bie II]]` te një homonim; `[[ajkos#2]]` te
  kuptimi 2 i saj; `[[bie II#3|ra]]` shfaq «ra» dhe çon te kuptimi 3 i «bie II».

### Një shembull më i plotë

Mbiemri «acar», që në origjinal vjen pas `•` te emri «acar»: kuptimi i dytë është i
figurshëm dhe ka një nënkuptim.

```json
{
  "id": "c81070ca-afde-50a7-8f54-afdd4467d071",
  "lemma": "acar",
  "pos": "mb",
  "source": "acar • acar",
  "grammar": {
    "Adjective": {
      "feminine": "acare"
    }
  },
  "family": {
    "id": "51da83e0-5819-5ff1-a298-64639aeebede",
    "lemma": "acar"
  },
  "senses": [
    {
      "definition": "i acartë",
      "examples": [
        {
          "text": "erë acare"
        }
      ]
    },
    {
      "definition": "shumë i kthjellët",
      "labels": {
        "figurative": "fig"
      },
      "examples": [
        {
          "text": "ujë acar"
        }
      ],
      "subsenses": [
        {
          "definition": "shumë i pastër e i rregullt (*kryes.* në të veshur)"
        }
      ]
    }
  ]
}
```

Dhe një trajtë vetvetore, e lidhur me kuptimin 2 të foljes së saj:

```json
{
  "id": "5ae1547c-3180-5353-9d31-b778d6e2a701",
  "lemma": "ajkoset",
  "pos": "fol",
  "source": "ajkos • ajkoset",
  "grammar": {
    "Verb": {
      "third_person_only": true,
      "voice": "vetv"
    }
  },
  "family": {
    "id": "7c597666-cf06-52f4-a093-eb667fac86ae",
    "lemma": "ajkos"
  },
  "senses": [
    {
      "definition": "e [[ajkos#2]]",
      "labels": {
        "grammar": [
          "vetv"
        ]
      },
      "relations": [
        {
          "kind": "jovepr",
          "target": {
            "id": "7c597666-cf06-52f4-a093-eb667fac86ae",
            "lemma": "ajkos",
            "senses": [
              "2"
            ]
          }
        }
      ]
    },
    {
      "definition": "zbutet e bëhet si ajkë",
      "examples": [
        {
          "text": "u ajkos salca"
        },
        {
          "text": "u ajkosën fiqtë"
        }
      ]
    }
  ]
}
```

## Kodet

Kodet janë shkurtimet e vetë fjalorit, pa pikë. Tabelat tregojnë vetëm kodet që dalin në
këtë skedar dhe sa herë.

### Pjesa e ligjëratës (`pos`)

| Kodi | Kuptimi | Sa herë |
|---|---|---:|
| *(mungon)* | E papërcaktuar | 35 |
| `em` | Emër | 23.207 |
| `mb` | Mbiemër | 11.077 |
| `fol` | Folje | 8.641 |
| `ndajf` | Ndajfolje | 1.876 |
| `përem` | Përemër | 180 |
| `num` | Numëror | 39 |
| `parafj` | Parafjalë | 109 |
| `lidh` | Lidhëz | 92 |
| `pj` | Pjesëz | 116 |
| `pasth` | Pasthirrmë | 88 |
| `onomat` | Onomatope | 12 |
| `nyje` | Nyje | 2 |
| `fjalëform` | Element fjalëformues | 76 |
| `shkronjë` | Shkronjë | 36 |

### Emri: gjinia (`gender`), numri (`number`)

| Kodi | Kuptimi | Sa herë |
|---|---|---:|
| *(mungon)* | E papërcaktuar | 70 |
| `m` | Mashkullore | 10.588 |
| `f` | Femërore | 12.347 |
| `as` | Asnjanëse | 202 |

| Kodi | Kuptimi | Sa herë |
|---|---|---:|
| *(mungon)* | Njëjës dhe shumës | 22.936 |
| `nj` | Vetëm njëjës | 2 |
| `sh` | Vetëm shumës | 269 |

### Nyja e përparme (`article`, te emrat dhe mbiemrat)

| Kodi | Kuptimi | Sa herë |
|---|---|---:|
| *(mungon)* | Pa nyje | 28.949 |
| `i` | i | 80 |
| `e` | e | 255 |
| `i,e` | i, e | 4.767 |
| `të` | të | 233 |

### Folja: kalueshmëria (`transitivity`) dhe diateza (`voice`)

| Kodi | Kuptimi | Sa herë |
|---|---|---:|
| *(mungon)* | E papërcaktuar | 4.332 |
| `kal` | Kalimtare | 3.453 |
| `jokal` | Jokalimtare | 709 |
| `kal,jokal` | Kalimtare dhe jokalimtare | 147 |

| Kodi | Kuptimi | Sa herë |
|---|---|---:|
| *(mungon)* | Veprore | 4.408 |
| `vetv` | Vetvetore | 2.687 |
| `pës` | Pësore | 1.546 |

### Lloji i përemrit dhe i elementit fjalëformues (`kind`)

| Kodi | Kuptimi | Sa herë |
|---|---|---:|
| *(mungon)* | E papërcaktuar | 30 |
| `vetor` | Vetor | 5 |
| `dëft` | Dëftor | 6 |
| `pron` | Pronor | 17 |
| `pyet` | Pyetës | 4 |
| `lidhor` | Lidhor | 4 |
| `pacak` | I pacaktuar | 106 |
| `pakuf` | I pakufishëm | 8 |

| Kodi | Kuptimi | Sa herë |
|---|---|---:|
| *(mungon)* | Parashtesë | 14 |
| `gjymtyrë.1` | Gjymtyrë e parë e fjalëve të përbëra | 58 |
| `gjymtyrë.2` | Gjymtyrë e dytë e fjalëve të përbëra | 4 |

### Ligjërimi (`labels.register`)

| Kodi | Kuptimi | Sa herë |
|---|---|---:|
| `bised` | Bisedore | 2.403 |
| `libr` | Librore | 1.770 |
| `zyrt` | Zyrtare | 83 |
| `poet` | Poetike | 137 |
| `lart` | Stil i lartë | 69 |
| `thjesht` | Ligjërim i thjeshtë | 66 |
| `fëm` | Fëminore | 13 |
| `spec` | Term special | 347 |

### Ngjyrimi (`labels.attitude`)

| Kodi | Kuptimi | Sa herë |
|---|---|---:|
| `keq` | Keqësuese | 973 |
| `mospërf` | Mospërfillëse | 332 |
| `përçm` | Përçmuese | 62 |
| `përb` | Përbuzëse | 51 |
| `shar` | Sharëse | 132 |
| `iron` | Ironike | 181 |
| `tall` | Tallëse | 47 |
| `shak` | Me shaka | 39 |
| `përk` | Përkëdhelëse | 83 |
| `zvog` | Zvogëluese | 8 |
| `euf` | Eufemizëm | 129 |
| `përf` | Përforcuese | 47 |
| `mallk` | Mallkim | 16 |
| `ur` | Urim | 1 |

### Koha dhe shpeshtësia (`labels.time`, `labels.usage`)

| Kodi | Kuptimi | Sa herë |
|---|---|---:|
| `vjet` | E vjetruar | 406 |

| Kodi | Kuptimi | Sa herë |
|---|---|---:|
| `kryes` | Kryesisht | 623 |
| `zakon` | Zakonisht | 109 |
| `rrallë` | Rrallë | 1 |

### Kuptimi i figurshëm (`labels.figurative`)

| Kodi | Kuptimi | Sa herë |
|---|---|---:|
| `fig` | Kuptim i figurshëm | 3.883 |
| `edhe.fig` | Edhe në kuptim të figurshëm | 646 |

### Kushtet gramatikore (`labels.grammar`)

| Kodi | Kuptimi | Sa herë |
|---|---|---:|
| `kal` | Kalimtare | 149 |
| `jokal` | Jokalimtare | 274 |
| `edhe.kal` | Edhe kalimtare | 62 |
| `edhe.jokal` | Edhe jokalimtare | 143 |
| `vetv` | Vetvetore | 207 |
| `pës` | Pësore | 1.059 |
| `pavet` | Pavetore | 46 |
| `v3` | Vetëm në vetën e tretë | 984 |
| `sh` | Në shumës | 802 |
| `nj` | Në njëjës | 123 |
| `shquar` | Në trajtën e shquar | 12 |
| `f` | Në femërore | 13 |
| `përmb` | Përmbledhës | 224 |
| `moh` | Në fjali mohore | 6 |
| `trajtë.shkurt` | Me trajtë të shkurtër përemërore | 153 |
| `kallëz` | Si kallëzuesor | 19 |
| `si.em` | Si emër | 9 |
| `edhe.si.em` | Edhe si emër | 2.718 |
| `si.em.m` | Si emër mashkullor | 5 |
| `si.em.f` | Si emër femëror | 14 |
| `edhe.si.em.m` | Edhe si emër mashkullor | 69 |
| `edhe.si.em.f` | Edhe si emër femëror | 70 |
| `si.mb` | Si mbiemër | 292 |
| `edhe.si.mb` | Edhe si mbiemër | 498 |
| `si.ndajf` | Si ndajfolje | 291 |
| `edhe.si.ndajf` | Edhe si ndajfolje | 44 |
| `si.pasth` | Si pasthirrmë | 15 |
| `palak` | E palakueshme | 7 |

### Zona (`labels.areas.dialects`)

| Kodi | Kuptimi | Sa herë |
|---|---|---:|
| `krahin` | Krahinore | 316 |
| `arb` | Arbëreshe | 17 |

### Lloji i shembullit dhe i shprehjes (`kind`)

Shembujt:

| Kodi | Kuptimi | Sa herë |
|---|---|---:|
| *(mungon)* | Shembull përdorimi | 47.531 |
| `fj.u` | Fjalë e urtë | 870 |
| `ur` | Urim | 115 |
| `mallk` | Mallkim | 57 |
| `betim` | Betim | 7 |

Shprehjet:

| Kodi | Kuptimi | Sa herë |
|---|---|---:|
| *(mungon)* | Shprehje frazeologjike | 4.727 |
| `fj.u` | Fjalë e urtë | 1 |
| `ur` | Urim | 10 |
| `mallk` | Mallkim | 9 |

### Lloji i lidhjes (`relations[].kind`)

| Kodi | Kuptimi | Sa herë |
|---|---|---:|
| `sin` | Sinonim | 416 |
| `kund` | Antonim | 1.935 |
| `fem` | Femërorja e | 1.350 |
| `mashk` | Mashkullorja e | 4 |
| `zvog` | Zvogëlim i | 3 |
| `jovepr` | Trajta joveprore e | 2.953 |
| `vepr` | Trajta veprore e | 2 |
| *(mungon)* | Shih edhe | 99 |

### Lloji i shënimit (`notes[].kind`)

| Kodi | Kuptimi | Sa herë |
|---|---|---:|
| *(mungon)* | Përdorimi | 21 |
| `gram` | Gramatika | 122 |

### Tiparet e trajtave (`forms[].features`)

`nj` Njëjës (14) · `sh` Shumës (50) · `shquar` E shquar (20) · `pashquar` E pashquar (9) · `r.gj` Gjinore (18) · `r.dh` Dhanore (33) · `r.k` Kallëzore (36) · `r.rr` Rrjedhore (23) · `m` Mashkullore (25) · `f` Femërore (33) · `as` Asnjanëse (1) · `v1` Veta I (1) · `v3` Veta III (2) · `dëft` Dëftore (1) · `urdh` Urdhërore (1) · `kr.thj` E kryer e thjeshtë (2) · `pjes` Pjesore (2) · `jovepr` Joveprore (2) · `shkurt` Trajtë e shkurtër (14)

### Fusha (`labels.domains`)

`anat` Anatomi (290) · `antrop` Antropologji (1) · `arkeol` Arkeologji (11) · `arkit` Arkitekturë (21) · `art` Art (80) · `astr` Astronomi (66) · `astrol` Astrologji (10) · `av` Aviacion (13) · `biokim` Biokimi (2) · `biol` Biologji (126) · `blet` Bletari (8) · `bot` Botanikë (1.263) · `bujq` Bujqësi (93) · `det` Detari (27) · `dipl` Diplomaci (34) · `drejt` Drejtësi (226) · `ek` Ekonomi (101) · `elektr` Elektronikë (88) · `etnogr` Etnografi (234) · `farm` Farmaceutikë (18) · `fet` Fe (307) · `filoz` Filozofi (126) · `fin` Financë (117) · `fiz` Fizikë (229) · `fiziol` Fiziologji (36) · `folk` Folklor (30) · `foto` Fotografi (3) · `gjah` Gjueti (4) · `gjell` Gjellëtari (135) · `gjeod` Gjeodezi (6) · `gjeofiz` Gjeofizikë (1) · `gjeogr` Gjeografi (102) · `gjeol` Gjeologji (70) · `gjeom` Gjeometri (114) · `gjuh` Gjuhësi (595) · `hek` Hekurudha (4) · `hidrol` Hidrologji (1) · `hidrotek` Hidroteknikë (7) · `hist` Histori (397) · `kim` Kimi (207) · `kinem` Kinematografi (11) · `kirur` Kirurgji (2) · `kish` Kishë (2) · `kompj` Kompjuter (18) · `let` Letërsi (213) · `letër` Lojë me letra (8) · `logj` Logjikë (21) · `mat` Matematikë (172) · `mek` Mekanikë (5) · `meteor` Meteorologji (18) · `min` Mineralogji e miniera (53) · `mit` Mitologji (98) · `mjek` Mjekësi (402) · `muz` Muzikë (171) · `ndërt` Ndërtimtari (46) · `opt` Optikë (11) · `paleont` Paleontologji (2) · `peshk` Peshkatari (2) · `polit` Politikë (1) · `psikol` Psikologji (37) · `pyllt` Pylltari (1) · `radio` Radioteknikë (4) · `shah` Shah (9) · `shtypshkr` Shtypshkronjë (31) · `sport` Sport (250) · `teatër` Teatër (29) · `tek` Teknikë (306) · `tekst` Tekstile (10) · `telev` Televizion (1) · `treg` Tregti (6) · `usht` Ushtri (351) · `veter` Veterinari (106) · `zool` Zoologji (888)

## Shifra

| | |
|---|---:|
| Fjalë | 45.586 |
| nga të cilat pas `•` në origjinal (me `family`) | 14.781 |
| Kuptime | 57.840 |
| Nënkuptime | 2.543 |
| Shembuj | 48.579 |
| Shprehje | 4.747 |
| Fjalë me lidhje (`relations`) te vetja | 2.916 |
| Fjalë me homonim të numëruar | 1.087 |

## Kufizime të njohura

- 35 fjalë nuk kanë pjesë ligjërate, sepse origjinali nuk e jep.
- 172 lidhje çojnë te një fjalë që nuk është zë i fjalorit (`target` pa `id`).
- 2.650 lema kanë më shumë se një hyrje (p.sh. emri dhe mbiemri «acar»); numër homonimi
  kanë vetëm ato që origjinali i numëron.
- Disa shkurtime kanë mbetur si tekst brenda shpjegimit (p.sh. «(*kryes.* në të veshur)»),
  aty ku nuk vlejnë për gjithë kuptimin.
- Jepen vetëm trajtat që jep origjinali (trajta e shquar, shumësi, femërorja, e kryera e
  thjeshtë, pjesorja); lakimi dhe zgjedhimi i plotë nuk janë pjesë e skedarit.
- Gabime mund të kenë mbetur. Ndreqjet bëhen në fjalor.com dhe vijnë këtu me shkarkimin
  tjetër.
