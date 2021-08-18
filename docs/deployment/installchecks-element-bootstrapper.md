---
title: '&lt;Elemento InstallChecks &gt; (programma di avvio automatico) | Microsoft Docs'
description: L'elemento InstallChecks supporta l'avvio di un'ampia gamma di test nel computer locale per assicurarsi che siano stati installati tutti i prerequisiti per un'applicazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <InstallChecks> element [bootstrapper]
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 0f2487489d75ca4ce7275153fd754b6fac7ebf5e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051573"
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;Elemento InstallChecks &gt; (programma di avvio automatico)
L'elemento supporta l'avvio di un'ampia gamma di test nel computer locale per assicurarsi che siano stati installati tutti i prerequisiti appropriati per `InstallChecks` un'applicazione.

## <a name="syntax"></a>Sintassi

```xml
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

## <a name="assemblycheck"></a>Controllo assembly
 Questo elemento è un elemento figlio facoltativo di `InstallChecks` . Per ogni istanza di , il programma di avvio automatico verifica che l'assembly identificato dall'elemento `AssemblyCheck` esista nella Global Assembly Cache (GAC). Non contiene elementi e ha gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`Property`|Obbligatorio. Nome della proprietà in cui archiviare il risultato. È possibile fare riferimento a questa proprietà da un test sotto `InstallConditions` l'elemento , che è un elemento figlio `Command` dell'elemento . Per altre informazioni, vedere [ \<Commands> Elemento](../deployment/commands-element-bootstrapper.md).|
|`Name`|Obbligatorio. Nome completo dell'assembly da controllare.|
|`PublicKeyToken`|Obbligatorio. Forma abbreviata della chiave pubblica associata a questo assembly con nome sicuro. Tutti gli assembly archiviati nella GAC devono avere un nome, una versione e una chiave pubblica.|
|`Version`|Obbligatorio. Versione dell'assembly.<br /><br /> Il numero di versione ha il \<*major version*> formato . . . \<*minor version*> \<*build version*> \<*revision version*> .|
|`Language`|facoltativo. Lingua di un assembly localizzato. Il valore predefinito è `neutral`.|
|`ProcessorArchitecture`|facoltativo. Processore del computer di destinazione dell'installazione. Il valore predefinito è `msil`.|

## <a name="externalcheck"></a>Controllo esterno
 Questo elemento è un elemento figlio facoltativo di `InstallChecks` . Per ogni istanza di , il programma di avvio automatico eseguirà il programma esterno denominato in un processo separato e archivierà il codice di uscita nella proprietà `ExternalCheck` indicata da `Property` . `ExternalCheck` è utile per implementare controlli delle dipendenze complessi o quando l'unico modo per verificare l'esistenza di un componente è crearne un'istanza.

 `ExternalCheck` non contiene elementi e dispone degli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`Property`|Obbligatorio. Nome della proprietà in cui archiviare il risultato. È possibile fare riferimento a questa proprietà da un test sotto `InstallConditions` l'elemento , che è un elemento figlio `Command` dell'elemento . Per altre informazioni, vedere [ \<Commands> Elemento](../deployment/commands-element-bootstrapper.md).|
|`PackageFile`|Obbligatorio. Programma esterno da eseguire. Il programma deve far parte del pacchetto di distribuzione dell'installazione.|
|`Arguments`|facoltativo. Fornisce argomenti della riga di comando all'eseguibile denominato da `PackageFile` .|

## <a name="filecheck"></a>FileCheck
 Questo elemento è un elemento figlio facoltativo di `InstallChecks` . Per ogni istanza di , il programma di avvio automatico determina se il file denominato esiste e `FileCheck` restituisce il numero di versione del file. Se il file non ha un numero di versione, il programma di avvio automatico imposta la proprietà denominata `Property` da su 0. Se il file non esiste, `Property` non è impostato su alcun valore.

 `FileCheck` non contiene elementi e dispone degli attributi seguenti.

| Attributo | Descrizione |
|-----------------| - |
| `Property` | Obbligatorio. Nome della proprietà in cui archiviare il risultato. È possibile fare riferimento a questa proprietà da un test sotto `InstallConditions` l'elemento , che è un elemento figlio `Command` dell'elemento . Per altre informazioni, vedere [ \<Commands> Elemento](../deployment/commands-element-bootstrapper.md). |
| `FileName` | Obbligatorio. Nome del file da trovare. |
| `SearchPath` | Obbligatorio. Disco o cartella in cui cercare il file. Deve trattarsi di un percorso relativo `SpecialFolder` se è assegnato; in caso contrario, deve essere un percorso assoluto. |
| `SpecialFolder` | facoltativo. Cartella che ha un significato particolare da Windows o a [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . L'impostazione predefinita è `SearchPath` l'interpretazione come percorso assoluto. I valori validi sono i seguenti:<br /><br /> `AppDataFolder`. Cartella dei dati dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per questa applicazione, specifica dell'utente corrente.<br /><br /> `CommonAppDataFolder`. Cartella dei dati dell'applicazione usata da tutti gli utenti.<br /><br /> `CommonFilesFolder`. Cartella File comuni per l'utente corrente.<br /><br /> `LocalDataAppFolder`. Cartella di dati per le applicazioni non in roaming.<br /><br /> `ProgramFilesFolder`. Cartella Programmi standard per le applicazioni a 32 bit.<br /><br /> `StartUpFolder`. Cartella che contiene tutte le applicazioni avviate all'avvio del sistema.<br /><br /> `SystemFolder`. Cartella che contiene DLL di sistema a 32 bit.<br /><br /> `WindowsFolder`. Cartella che contiene l'Windows di sistema.<br /><br /> `WindowsVolume`. L'unità o la partizione che contiene l Windows installazione del sistema. |
| `SearchDepth` | facoltativo. Profondità in base alla quale cercare il file denominato nelle sottocartelle. La ricerca è depth-first. Il valore predefinito è 0, che limita la ricerca alla cartella di primo livello specificata da `SpecialFolder` e **SearchPath.** |

## <a name="msiproductcheck"></a>MsiProductCheck
 Questo elemento è un elemento figlio facoltativo di `InstallChecks` . Per ogni istanza di , il programma di avvio automatico verifica se l'installazione di Microsoft Windows Installer specificata è stata eseguita `MsiProductCheck` fino al completamento. Il valore della proprietà viene impostato a seconda dello stato del prodotto installato. Un valore positivo indica che il prodotto è installato, 0 o -1 indica che non è installato. Per altre informazioni, Windows la funzione msiQueryFeatureState dell'SDK del programma di installazione. . Se Windows installer non è installato nel computer, `Property` non è impostato.

 `MsiProductCheck` non contiene elementi e dispone degli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`Property`|Obbligatorio. Nome della proprietà in cui archiviare il risultato. È possibile fare riferimento a questa proprietà da un test sotto `InstallConditions` l'elemento , che è un elemento figlio `Command` dell'elemento . Per altre informazioni, vedere [ \<Commands> Elemento](../deployment/commands-element-bootstrapper.md).|
|`Product`|Obbligatorio. GUID del prodotto installato.|
|`Feature`|facoltativo. GUID per una funzionalità specifica dell'applicazione installata.|

## <a name="registrycheck"></a>Controllo del Registro di sistema
 Questo elemento è un elemento figlio facoltativo di `InstallChecks` . Per ogni istanza di , il programma di avvio automatico verifica se la chiave del Registro di sistema specificata esiste o `RegistryCheck` se ha il valore indicato.

 `RegistryCheck` non contiene elementi e dispone degli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`Property`|Obbligatorio. Nome della proprietà in cui archiviare il risultato. È possibile fare riferimento a questa proprietà da un test sotto l'elemento , che `InstallConditions` è un elemento figlio dell'elemento `Command` . Per altre informazioni, vedere [ \<Commands> Elemento](../deployment/commands-element-bootstrapper.md).|
|`Key`|Obbligatorio. Nome della chiave del Registro di sistema.|
|`Value`|facoltativo. Nome del valore del Registro di sistema da recuperare. L'impostazione predefinita è restituire il testo del valore predefinito. `Value` deve essere una stringa o un valore DWORD.|

## <a name="registryfilecheck"></a>RegistryFileCheck
 Questo elemento è un elemento figlio facoltativo di `InstallChecks` . Per ogni istanza di , il programma di avvio automatico recupera la versione del file specificato, tentando prima di recuperare il percorso del file dalla chiave del Registro `RegistryFileCheck` di sistema specificata. Ciò è particolarmente utile se si vuole cercare un file in una directory specificata come valore nel Registro di sistema.

 `RegistryFileCheck` non contiene elementi e dispone degli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`Property`|Obbligatorio. Nome della proprietà in cui archiviare il risultato. È possibile fare riferimento a questa proprietà da un test sotto l'elemento , che `InstallConditions` è un elemento figlio dell'elemento `Command` . Per altre informazioni, vedere [ \<Commands> Elemento](../deployment/commands-element-bootstrapper.md).|
|`Key`|Obbligatorio. Nome della chiave del Registro di sistema. Il valore viene interpretato come percorso di un file, a meno che `File` l'attributo non sia impostato. Se questa chiave non esiste, `Property` non è impostata.|
|`Value`|facoltativo. Nome del valore del Registro di sistema da recuperare. L'impostazione predefinita è restituire il testo del valore predefinito. `Value` deve essere un valore String.|
|`FileName`|facoltativo. Nome di un file. Se specificato, si presuppone che il valore ottenuto dalla chiave del Registro di sistema sia un percorso di directory e questo nome viene aggiunto. Se non specificato, si presuppone che il valore restituito dal Registro di sistema sia il percorso completo di un file.|
|`SearchDepth`|facoltativo. Profondità in base alla quale cercare il file denominato nelle sottocartelle. La ricerca è depth-first. Il valore predefinito è 0, che limita la ricerca alla cartella di primo livello specificata dal valore della chiave del Registro di sistema.|

## <a name="remarks"></a>Commenti
 Mentre gli elementi `InstallChecks` sottostanti definiscono i test da eseguire, non li eseguono. Per eseguire i test, è necessario creare `Command` elementi sotto `Commands` l'elemento .

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene `InstallChecks` illustrato l'elemento usato nel file del prodotto per l'.NET Framework.

```xml
<InstallChecks>
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />
</InstallChecks>
```

## <a name="installconditions"></a>InstallConditions
 Quando `InstallChecks` vengono valutate, producono proprietà. Le proprietà vengono quindi usate da per determinare se un pacchetto deve essere `InstallConditions` installato, ignorato o non riuscito. Nella tabella seguente sono elencati `InstallConditions` i seguenti elementi:

|Condizione|Descrizione|
|-|-|
|`FailIf`|Se una `FailIf` condizione restituisce true, il pacchetto avrà esito negativo. Le altre condizioni non verranno valutate.|
|`BypassIf`|Se una `BypassIf` condizione restituisce true, il pacchetto verrà ignorato. Le altre condizioni non verranno valutate.|

## <a name="predefined-properties"></a>Proprietà predefinite
 Nella tabella seguente sono elencati `BypassIf` gli elementi `FailIf` e :

|Proprietà|Note|Valori possibili|
|--------------|-----------|---------------------|
|`Version9X`|Numero di versione di un Windows 9X.|4.10 = Windows 98|
|`VersionNT`|Numero di versione di Windows NT sistema operativo basato su .|Major.Minor.ServicePack<br /><br /> 5.0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professional SP2<br /><br /> 5.2.0 = Windows Server 2003|
|`VersionNT64`|Numero di versione di un sistema operativo Windows NT a 64 bit.|Come accennato in precedenza.|
|`VersionMsi`|Numero di versione del servizio Windows Installer.|2.0 = Windows Installer 2.0|
|`AdminUser`|Specifica se un utente dispone dei privilegi di amministratore in un Windows NT sistema operativo basato su computer.|0 = nessun privilegio di amministratore<br /><br /> 1 = privilegi di amministratore|

 Ad esempio, per bloccare l'installazione in un computer che esegue Windows 95, usare codice simile al seguente:

```xml
    <!-- Block install on Windows 95 -->
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>
```

 Per ignorare l'esecuzione dei controlli di installazione se viene soddisfatta una condizione FailIf o BypassIf, usare l'attributo BeforeInstallChecks.  Esempio:

```xml
    <!-- Block install and do not evaluate install checks if user does not have admin privileges -->
    <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired" BeforeInstallChecks="true"/>
```

>[!NOTE]
>`BeforeInstallChecks`L'attributo è supportato a partire dalla versione Visual Studio 2019 Update 9.

## <a name="see-also"></a>Vedi anche
- [\<Commands> Elemento](../deployment/commands-element-bootstrapper.md)
- [Informazioni di riferimento sullo schema di prodotti e pacchetti](../deployment/product-and-package-schema-reference.md)