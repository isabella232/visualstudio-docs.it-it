---
title: Compilatore dei colori VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e1607ec4863c7e2b21cd69dd57ca4203e3cf4dbf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68147939"
---
# <a name="vsix-color-compiler"></a>Compilatore dei colori VSIX
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lo strumento compilatore di Visual Studio estensione colore è un'applicazione console che accetta un file con estensione XML che rappresenta i colori per i temi di Visual Studio esistenti e vengono convertiti in un pkgdef file in modo che questi colori possono essere usati in Visual Studio. Poiché è facile confrontare le differenze tra file con estensione XML, questo strumento è utile per la gestione dei colori personalizzati nel controllo del codice sorgente. Anche possibile eseguire l'hook al ambienti di compilazione in modo che l'output della compilazione è un file. pkgdef valido.  
  
 **Schema XML del tema**  
  
 Un file con estensione XML tema completo è simile alla seguente:  
  
```xml  
<Themes>  
      <!—one or Theme elements -->  
      <Theme>  
        <!-- one or more Category elements -->  
        <Category>  
          <!-- one or more Color elements -->  
          <Color>  
            <!-- zero or one Background element -->  
            <Background />  
            <!-- zero or one Foreground element -->  
            <Foreground />  
          </Color>  
        </Category>  
      </Theme>  
</Themes>  
```  
  
 **Tema**  
  
 Il \<tema > elemento definisce un tema completo. Un tema deve contenere almeno un \<categoria > elemento. Elementi dei temi sono definiti come segue:  
  
```xml  
<Theme Name="name" GUID="guid">  
      <!-- one or more Category elements -->  
</Theme>  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|Name|[Obbligatorio] Il nome del tema|  
|GUID|[Obbligatorio] GUID del tema (deve corrispondere la formattazione di GUID)|  
  
 Durante la creazione di colori personalizzati per Visual Studio, questi colori devono essere definiti per i seguenti temi. Se è presente alcun colore per un particolare tema, Visual Studio tenta di caricare i colori mancanti dal tema chiaro.  
  
|||  
|-|-|  
|**Nome del tema**|**Tema GUID**|  
|Chiaro|{de3dbbcd-f642-433c-8353-8f1df4370aba}|  
|Scuro|{1ded0138-47ce-435e-84ef-9ec1f439b749}|  
|Blu|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
|Contrasto elevato|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
  
 **Categoria**  
  
 Il \<categoria > elemento definisce una raccolta di colori in un tema. Nomi di categoria offrono raggruppamenti logici e devono essere definiti come ristretto possibile. Una categoria deve contenere almeno un \<colore > elemento. Elementi delle categorie sono definiti come segue:  
  
```xml  
<Category Name="name" GUID="guid">  
      <!-- one or more Color elements -->  
 </Category>  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|Name|[Obbligatorio] Il nome della categoria|  
|GUID|[Obbligatorio] GUID della categoria (deve corrispondere la formattazione di GUID)|  
  
 **Colore**  
  
 Il \<colore > elemento definisce un colore di un componente o lo stato dell'interfaccia utente. Lo schema di denominazione preferito per un colore è [tipo di interfaccia utente] [stato]. Non usare la parola "color", perché è ridondante. Un colore debba indicare chiaramente il tipo di elemento e le situazioni o "state", per il quale verrà applicato il colore. Un colore non deve essere vuoto e deve contenere uno o entrambi una \<sfondo > e \<in primo piano > elemento. Elementi di colore sono definiti come segue:  
  
```xml  
<Color Name="name">  
        <Background /> <!-- zero or one Background element -->  
        <Foreground /> <!-- zero or one Foreground element -->  
 </Color>  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|Name|[Obbligatorio] Il nome del colore|  
  
 **Sfondo e/o in primo piano**  
  
 Il \<sfondo > e \<in primo piano > elementi che definiscono un colore valore e tipo di primo piano di un elemento dell'interfaccia utente o in background. Questi elementi non dispongono di nessun elemento figlio.  
  
```xml  
<Background Type="type" Source="int" />  
<Foreground Type="type" Source="int" />  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|Type|[Obbligatorio] Il tipo del colore. Può essere uno dei seguenti:<br /><br /> *CT_INVALID:* Il colore non valido o non impostata.<br /><br /> *CT_RAW:* Un valore ARGB non elaborato.<br /><br /> *CT_COLORINDEX:* NON USARE.<br /><br /> *CT_SYSCOLOR:* Un colore di sistema di Windows da SysColor.<br /><br /> *CT_VSCOLOR:* Un colore di Visual Studio da __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* Colore automatico.<br /><br /> *CT_TRACK_FOREGROUND:* NON USARE.<br /><br /> *CT_TRACK_BACKGROUND:* NON USARE.|  
|Source|[Obbligatorio] Il valore del colore rappresentato in formato esadecimale|  
  
 Tutti i valori supportati dall'enumerazione __VSCOLORTYPE sono supportati per lo schema nell'attributo Type. Tuttavia, è consigliabile utilizzare solo CT_RAW e CT_SYSCOLOR.  
  
 **Tutti insieme**  
  
 Questo è un esempio semplice di un file con estensione XML di tema validi:  
  
```xml  
<Themes>  
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">  
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">  
      <Color Name="MyActiveBorder">  
        <Background Type="CT_RAW" Source="FFCCCEDB" />  
      </Color>  
    </Category>  
  </Theme>  
</Themes>  
```  
  
## <a name="how-to-use-the-tool"></a>Come usare lo strumento  
 **Sintassi**  
  
 VsixColorCompiler \<file XML > \<file PkgDef > \<Args facoltativo >  
  
 **Argomenti**  
  
||||  
|-|-|-|  
|**Nome del commutatore**|**Note**|**Obbligatoria o facoltativa**|  
|Senza nome (file con estensione XML)|Questo è il primo parametro senza nome e percorso del file XML da convertire.|Obbligatoria|  
|Senza nome (file con estensione pkgdef)|Questo è il secondo parametro senza nome e il percorso di output per il file. pkgdef generato.<br /><br /> Valore predefinito: \<Nome del file XML > con estensione pkgdef|Facoltativo|  
|/noLogo|Impostazione di questo flag arresta prodotto e informazioni sul copyright di stampare le informazioni.|Facoltativo|  
|/?|Stampare le informazioni della Guida.|Facoltativo|  
|/help|Stampare le informazioni della Guida.|Facoltativo|  
  
 **Esempi**  
  
- VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef  
  
- /NoLogo VsixColorCompiler D:\xml\colors.xml  
  
## <a name="notes"></a>Note  
  
- Questo strumento richiede che essere installata la versione più recente del runtime VC + +.  
  
- Sono supportati solo i file singoli. Non è supportata la conversione in blocco tramite i percorsi delle cartelle.  
  
## <a name="sample-output"></a>Esempio di output  
 Il file con estensione pkgdef generato dallo strumento sarà simile alle seguenti chiavi:  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]  
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff  
  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]  
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff  
```
