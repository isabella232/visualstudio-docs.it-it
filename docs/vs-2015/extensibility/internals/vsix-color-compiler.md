---
title: Compilatore di colori VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c92fb2ad45bc0fb09c7e9bd8e87db38c13a99736
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546744"
---
# <a name="vsix-color-compiler"></a>Compilatore dei colori VSIX
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lo strumento compilatore colori estensione Visual Studio è un'applicazione console che accetta un file con estensione XML che rappresenta i colori dei temi di Visual Studio esistenti e lo converte in un file con estensione pkgdef in modo che tali colori possano essere utilizzati in Visual Studio. Poiché è facile confrontare le differenze tra i file con estensione XML, questo strumento è utile per la gestione dei colori personalizzati nel controllo del codice sorgente. Può anche essere collegato negli ambienti di compilazione in modo che l'output della compilazione sia un file con estensione pkgdef valido.  
  
 **XML Schema tema**  
  
 Un file con estensione XML del tema completo è simile al seguente:  
  
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
  
 L' \<Theme> elemento definisce un intero tema. Un tema deve contenere almeno un \<Category> elemento. Gli elementi del tema sono definiti come segue:  
  
```xml  
<Theme Name="name" GUID="guid">  
      <!-- one or more Category elements -->  
</Theme>  
```  
  
|**Attributo**|**Definizione**|  
|-|-|  
|Nome|Necessaria Nome del tema|  
|GUID|Necessaria Il GUID del tema (deve corrispondere alla formattazione del GUID)|  
  
 Quando si creano colori personalizzati per Visual Studio, è necessario definire questi colori per i temi seguenti. Se non esistono colori per un particolare tema, Visual Studio tenta di caricare i colori mancanti dal tema chiaro.  
  
|**Nome del tema**|**GUID tema**|  
|-|-|  
|Chiaro|{de3dbbcd-f642-433c-8353-8f1df4370aba}|  
|Scuro|{1ded0138-47ce-435e-84ef-9ec1f439b749}|  
|Blu|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
|Contrasto elevato|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
  
 **Categoria**  
  
 L' \<Category> elemento definisce una raccolta di colori in un tema. I nomi di categoria forniscono raggruppamenti logici e devono essere definiti nel modo più restrittivo possibile. Una categoria deve contenere almeno un \<Color> elemento. Gli elementi Category sono definiti come segue:  
  
```xml  
<Category Name="name" GUID="guid">  
      <!-- one or more Color elements -->  
 </Category>  
```  
    
|**Attributo**|**Definizione**|  
|-|-|  
|Nome|Necessaria Nome della categoria|  
|GUID|Necessaria Il GUID della categoria (deve corrispondere alla formattazione del GUID)|  
  
 **Colore**  
  
 L' \<Color> elemento definisce un colore per un componente o lo stato dell'interfaccia utente. Lo schema di denominazione preferito per un colore è [tipo interfaccia utente] [stato]. Non usare la parola "color", perché è ridondante. Un colore deve indicare chiaramente il tipo di elemento e le situazioni, o "stato", per cui verrà applicato il colore. Un colore non deve essere vuoto e deve contenere uno o entrambi gli \<Background> \<Foreground> elementi e. Gli elementi di colore sono definiti come segue:  
  
```xml  
<Color Name="name">  
        <Background /> <!-- zero or one Background element -->  
        <Foreground /> <!-- zero or one Foreground element -->  
 </Color>  
```  
  
|**Attributo**|**Definizione**|  
|-|-|  
|Nome|Necessaria Nome del colore|  
  
 **Sfondo e/o primo piano**  
  
 Gli \<Background> \<Foreground> elementi e definiscono il valore e il tipo di un colore per lo sfondo o il primo piano di un elemento dell'interfaccia utente. Questi elementi non hanno elementi figlio.  
  
```xml  
<Background Type="type" Source="int" />  
<Foreground Type="type" Source="int" />  
```  
  
|**Attributo**|**Definizione**|  
|-|-|  
|Type|Necessaria Tipo di colore. I possibili valori sono i seguenti:<br /><br /> *CT_INVALID:* Il colore non è valido o non è impostato.<br /><br /> *CT_RAW:* Valore ARGB non elaborato.<br /><br /> *CT_COLORINDEX:* NON USARE.<br /><br /> *CT_SYSCOLOR:* Colore di sistema Windows da SysColor.<br /><br /> *CT_VSCOLOR:* Colore di Visual Studio da __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* Colore automatico.<br /><br /> *CT_TRACK_FOREGROUND:* NON USARE.<br /><br /> *CT_TRACK_BACKGROUND:* NON USARE.|  
|Source (Sorgente)|Necessaria Valore del colore rappresentato in formato esadecimale|  
  
 Tutti i valori supportati dall'enumerazione __VSCOLORTYPE sono supportati dallo schema nell'attributo Type. È tuttavia consigliabile utilizzare solo CT_RAW e CT_SYSCOLOR.  
  
 **Tutto insieme**  
  
 Questo è un semplice esempio di file con estensione XML del tema valido:  
  
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
  
## <a name="how-to-use-the-tool"></a>Procedura: utilizzare lo strumento  
 **Sintassi**  
  
 VsixColorCompiler \<XML file> \<PkgDef file>\<Optional Args>  
  
 **Argomenti**  
  
|**Nome dell'opzione**|**Note**|**Obbligatorio o facoltativo**|  
|-|-|-|  
|Senza nome (file con estensione XML)|Si tratta del primo parametro senza nome e è il percorso del file XML da convertire.|Obbligatoria|  
|Senza nome (file. pkgdef)|Si tratta del secondo parametro senza nome e è il percorso di output per il file con estensione pkgdef generato.<br /><br /> Impostazione predefinita: \<XML Filename> . pkgdef|Facoltativo|  
|/noLogo|L'impostazione di questo flag interrompe le informazioni sul prodotto e sul copyright dalla stampa.|Facoltativo|  
|/?|Stampare le informazioni della guida.|Facoltativo|  
|/help|Stampare le informazioni della guida.|Facoltativo|  
  
 **Esempi**  
  
- VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef  
  
- VsixColorCompiler D:\xml\colors.xml/noLogo  
  
## <a name="notes"></a>Note  
  
- Per questo strumento è necessario che sia installata la versione più recente del runtime di VC + +.  
  
- Sono supportati solo i singoli file. La conversione bulk tramite percorsi di cartella non è supportata.  
  
## <a name="sample-output"></a>Output di esempio  
 Il file con estensione pkgdef generato dallo strumento sarà simile a quello riportato di seguito:  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]  
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff  
  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]  
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff  
```
