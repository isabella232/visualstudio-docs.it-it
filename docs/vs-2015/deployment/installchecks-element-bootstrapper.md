---
title: '&lt;InstallChecks&gt; elemento (programma di avvio automatico) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <InstallChecks> element [bootstrapper]
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: c4f5dde151993e7844cd9295d7aa16f7fd73327b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531339"
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;InstallChecks&gt; elemento (programma di avvio automatico)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [ &lt;InstallChecks&gt; elemento (programma di avvio automatico)](https://docs.microsoft.com/visualstudio/deployment/installchecks-element-bootstrapper).  
  
Il `InstallChecks` elemento supporta l'avvio di una serie di test sul computer locale per assicurarsi che siano stati installati tutti i prerequisiti appropriati per un'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<InstallChecks>  
    <AssemblyCheck   
        Property  
        Name  
        PublicKeyToken  
        Version  
        Language  
        ProcessorArchitecture  
    />  
    <RegistryCheck  
        Property  
        Key  
        Value  
    />  
    <ExternalCheck   
        PackageFile  
        Property  
        Arguments  
    />  
    <FileCheck   
        Property  
        FileName  
        SearchPath  
        SpecialFolder  
        SearchDepth  
    />  
    <MsiProductCheck   
        Property  
        Product  
        Feature  
    />  
    <RegistryFileCheck   
        Property  
        Key  
        Value  
        FileName  
        SearchDepth  
    />  
</InstallChecks>  
```  
  
## <a name="assemblycheck"></a>AssemblyCheck  
 Questo elemento è un elemento figlio facoltativo di `InstallChecks`. Per ogni istanza di `AssemblyCheck`, il programma di bootstrap garantirà che l'assembly identificato dall'elemento sia presente nella global assembly cache (GAC). Non contiene elementi e ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio. Il nome della proprietà per archiviare il risultato. Questa proprietà è possibile fare riferimento da un test sotto il `InstallConditions` elemento, che è un elemento figlio del `Command` elemento. Per altre informazioni, vedere [ \<comandi > elemento](../deployment/commands-element-bootstrapper.md).|  
|`Name`|Obbligatorio. Il nome completo dell'assembly da verificare.|  
|`PublicKeyToken`|Obbligatorio. La forma abbreviata della chiave pubblica associato a questo assembly un nome sicuro. Tutti gli assembly memorizzati nella Global Assembly Cache devono avere un nome, una versione e una chiave pubblica.|  
|`Version`|Obbligatorio. La versione dell'assembly.<br /><br /> Il numero di versione ha il formato \< *versione principale*>.\< *podverze*>.\< *versione build*>.\< *revisione*>.|  
|`Language`|Facoltativo. La lingua di un assembly localizzato. Il valore predefinito è `neutral`.|  
|`ProcessorArchitecture`|Facoltativo. Il processore del computer di destinazione dell'installazione. Il valore predefinito è `msil`.|  
  
## <a name="externalcheck"></a>ExternalCheck  
 Questo elemento è un elemento figlio facoltativo di `InstallChecks`. Per ogni istanza del `ExternalCheck`, il programma di bootstrap esegue il programma esterno denominato in un processo separato e archivierà il codice di uscita nella proprietà indicata da `Property`. `ExternalCheck` è utile per l'implementazione di controlli sulle dipendenze complesse oppure quando è l'unico modo per verificare l'esistenza di un componente a un'istanza.  
  
 `ExternalCheck` non contiene elementi e ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio. Il nome della proprietà per archiviare il risultato. Questa proprietà è possibile fare riferimento da un test sotto il `InstallConditions` elemento, che è un elemento figlio del `Command` elemento. Per altre informazioni, vedere [ \<comandi > elemento](../deployment/commands-element-bootstrapper.md).|  
|`PackageFile`|Obbligatorio. Il programma esterno per l'esecuzione. Il programma deve far parte del pacchetto di distribuzione di installazione.|  
|`Arguments`|Facoltativo. Fornisce gli argomenti della riga di comando per il file eseguibile denominato da `PackageFile`.|  
  
## <a name="filecheck"></a>FileCheck  
 Questo elemento è un elemento figlio facoltativo di `InstallChecks`. Per ogni istanza di `FileCheck`, il programma di bootstrap è determineranno se il file denominato esiste e restituire il numero di versione del file. Se il file non ha un numero di versione, il programma di avvio imposta la proprietà denominata da `Property` su 0. Se il file non esiste, `Property` non è impostata su qualsiasi valore.  
  
 `FileCheck` non contiene elementi e ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio. Il nome della proprietà per archiviare il risultato. Questa proprietà è possibile fare riferimento da un test sotto il `InstallConditions` elemento, che è un elemento figlio del `Command` elemento. Per altre informazioni, vedere [ \<comandi > elemento](../deployment/commands-element-bootstrapper.md).|  
|`FileName`|Obbligatorio. Il nome del file da trovare.|  
|`SearchPath`|Obbligatorio. Il disco o la cartella in cui cercare il file. Deve essere un percorso relativo se `SpecialFolder` assegnato; in caso contrario, deve essere un percorso assoluto.|  
|`SpecialFolder`|Facoltativo. Una cartella con un significato speciale in Windows o a [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. Il valore predefinito è l'interpretazione `SearchPath` come un percorso assoluto. Di seguito vengono elencati i valori validi:<br /><br /> `AppDataFolder`. La cartella application data per l'oggetto [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione; specifici dell'utente corrente.<br /><br /> `CommonAppDataFolder`. La cartella application data usata da tutti gli utenti.<br /><br /> `CommonFilesFolder`. Cartella file comuni per l'utente corrente.<br /><br /> `LocalDataAppFolder`. La cartella di dati per le applicazioni non comune.<br /><br /> `ProgramFilesFolder`. La cartella di file di programma standard per le applicazioni a 32 bit.<br /><br /> `StartUpFolder`. La cartella che contiene tutte le applicazioni avviate all'avvio del sistema.<br /><br /> `SystemFolder`. La cartella che contiene le DLL di sistema a 32 bit.<br /><br /> `WindowsFolder`. La cartella che contiene l'installazione del sistema Windows.<br /><br /> `WindowsVolume`. L'unità o partizione che contiene l'installazione del sistema Windows.|  
|`SearchDepth`|Facoltativo. La profondità in corrispondenza del quale eseguire la ricerca nelle sottocartelle per il file specificato. La ricerca è depth-first. Il valore predefinito è 0, che limita la ricerca nella cartella principale specificata dal `SpecialFolder` e **SearchPath**.|  
  
## <a name="msiproductcheck"></a>MsiProductCheck  
 Questo elemento è un elemento figlio facoltativo di `InstallChecks`. Per ogni istanza di `MsiProductCheck`, il programma di bootstrap controlla se l'installazione di Microsoft Windows Installer specificato è stato eseguito fino al completamento. Il valore della proprietà è impostato a seconda dello stato del prodotto installato. Un valore positivo indica il prodotto sia installato, 0 o -1 indica non è installato. (Vedere la funzione di Windows Installer SDK MsiQueryFeatureState per ulteriori informazioni). . Se Windows Installer non è installato nel computer, `Property` non è impostata.  
  
 `MsiProductCheck` non contiene elementi e ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio. Il nome della proprietà per archiviare il risultato. Questa proprietà è possibile fare riferimento da un test sotto il `InstallConditions` elemento, che è un elemento figlio del `Command` elemento. Per altre informazioni, vedere [ \<comandi > elemento](../deployment/commands-element-bootstrapper.md).|  
|`Product`|Obbligatorio. GUID per il prodotto installato.|  
|`Feature`|Facoltativo. Il GUID per funzionalità specifiche dell'applicazione installata.|  
  
## <a name="registrycheck"></a>RegistryCheck  
 Questo elemento è un elemento figlio facoltativo di `InstallChecks`. Per ogni istanza di `RegistryCheck`, il programma di bootstrap controlla se la chiave del Registro di sistema specificata esiste o se è impostata sul valore indicato.  
  
 `RegistryCheck` non contiene elementi e ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio. Il nome della proprietà per archiviare il risultato. Questa proprietà è possibile fare riferimento da un test sotto il `InstallConditions` elemento, che è un elemento figlio del `Command` elemento. Per altre informazioni, vedere [ \<comandi > elemento](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Obbligatorio. Nome della chiave del Registro di sistema.|  
|`Value`|Facoltativo. Il nome del valore del Registro di sistema da recuperare. Il valore predefinito è per restituire il testo del valore predefinito. `Value` deve essere una stringa o un valore DWORD.|  
  
## <a name="registryfilecheck"></a>RegistryFileCheck  
 Questo elemento è un elemento figlio facoltativo di `InstallChecks`. Per ogni istanza di `RegistryFileCheck`, il programma di bootstrap recupera la versione del file specificato, prima di tutto il tentativo di recuperare il percorso del file dalla chiave del Registro di sistema specificata. Ciò è particolarmente utile se si desidera cercare un file in una directory specificata come valore del Registro di sistema.  
  
 `RegistryFileCheck` non contiene elementi e ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio. Il nome della proprietà per archiviare il risultato. Questa proprietà è possibile fare riferimento da un test sotto il `InstallConditions` elemento, che è un elemento figlio del `Command` elemento. Per altre informazioni, vedere [ \<comandi > elemento](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Obbligatorio. Nome della chiave del Registro di sistema. Il valore viene interpretato come il percorso di un file, a meno che non la `File` attributo è impostato. Se questa chiave non esiste, `Property` non è impostata.|  
|`Value`|Facoltativo. Il nome del valore del Registro di sistema da recuperare. Il valore predefinito è per restituire il testo del valore predefinito. `Value` deve essere una stringa.|  
|`FileName`|Facoltativo. Il nome di un file. Se specificato, si presuppone che il valore ottenuto dalla chiave del Registro di sistema da un percorso di directory e questo nome viene aggiunto a esso. Se non specificato, il valore restituito dal Registro di sistema viene considerato il percorso completo in un file.|  
|`SearchDepth`|Facoltativo. La profondità in corrispondenza del quale eseguire la ricerca nelle sottocartelle per il file specificato. La ricerca è depth-first. Il valore predefinito è 0, che limita la ricerca per la cartella di primo livello specificata dal valore della chiave del Registro di sistema.|  
  
## <a name="remarks"></a>Note  
 Mentre gli elementi sotto `InstallChecks` definire i test da eseguire, essi non vengono eseguiti. Per eseguire i test, è necessario creare `Command` elementi di sotto di `Commands` elemento.  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra il `InstallChecks` elemento perché è usato nel file di prodotto per il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
```  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  
  
## <a name="installconditions"></a>InstallConditions  
 Quando `InstallChecks` vengono valutate, producono le proprietà. Le proprietà vengono quindi usate da `InstallConditions` per determinare se un pacchetto debba installare, ignorare o avere esito negativo. La tabella seguente elenca i `InstallConditions`:  
  
|||  
|-|-|  
|`FailIf`|Se qualsiasi `FailIf` condizione restituisce true, il pacchetto avrà esito negativo. Il resto delle condizioni non verrà valutato.|  
|`BypassIf`|Se qualsiasi `BypassIf` condizione restituisce true, il pacchetto verrà eseguito il bypass. Il resto delle condizioni non verrà valutato.|  
  
## <a name="predefined-properties"></a>Proprietà predefinite  
 La tabella seguente elenca i `BypassIf` e `FailIf` elementi:  
  
|Proprietà|Note|Valori possibili|  
|--------------|-----------|---------------------|  
|`Version9X`|Numero di versione del sistema operativo Windows 9 X.|4.10 = Windows 98|  
|`VersionNT`|Numero di versione del sistema operativo basato su Windows NT.|ServicePack<br /><br /> 5.0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professional SP2<br /><br /> 5.2.0 = Windows Server 2003|  
|`VersionNT64`|Numero di versione del sistema operativo a 64 bit basati su Windows NT.|Come indicato in precedenza.|  
|`VersionMsi`|Numero di versione del servizio Windows Installer.|2.0 = Windows Installer 2.0|  
|`AdminUser`|Specifica se un utente dispone di privilegi di amministratore in un sistema operativo basato su Windows NT.|0 non = privilegi di amministratore<br /><br /> 1 = i privilegi di amministratore|  
  
 Ad esempio, per bloccare l'installazione in un computer che eseguono Windows 95, usare codice simile al seguente:  
  
```  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [\<I comandi > elemento](../deployment/commands-element-bootstrapper.md)   
 [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)



