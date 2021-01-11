---
title: '&lt;&gt;Elemento InstallChecks (programma di avvio automatico) | Microsoft Docs'
description: L'elemento InstallChecks supporta l'avvio di una serie di test nel computer locale per assicurarsi che siano stati installati tutti i prerequisiti per un'applicazione.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf02fda50678d9de4eb01dc28b4825844e33063e
ms.sourcegitcommit: b1f7e7d7a0550d5c6f46adff3bddd44bc1d6ee1c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2021
ms.locfileid: "98069500"
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;&gt;Elemento InstallChecks (programma di avvio automatico)
L' `InstallChecks` elemento supporta l'avvio di una serie di test sul computer locale per assicurarsi che siano stati installati tutti i prerequisiti appropriati per un'applicazione.

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

## <a name="assemblycheck"></a>AssemblyCheck
 Questo elemento è un elemento figlio facoltativo di `InstallChecks` . Per ogni istanza di `AssemblyCheck` , il programma di avvio automatico verifica che l'assembly identificato dall'elemento esista nella global assembly cache (GAC). Non contiene elementi e ha gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`Property`|Obbligatorio. Nome della proprietà in cui archiviare il risultato. È possibile fare riferimento a questa proprietà da un test sotto l' `InstallConditions` elemento, che è figlio dell' `Command` elemento. Per ulteriori informazioni, vedere [ \<Commands> elemento](../deployment/commands-element-bootstrapper.md).|
|`Name`|Obbligatorio. Nome completo dell'assembly da verificare.|
|`PublicKeyToken`|Obbligatorio. Forma abbreviata della chiave pubblica associata a questo assembly con nome sicuro. Tutti gli assembly archiviati nella global assembly cache devono avere un nome, una versione e una chiave pubblica.|
|`Version`|Obbligatorio. Versione dell'assembly.<br /><br /> Il formato del numero di versione è.. \<*major version*> \<*minor version*> \<*build version*> . \<*revision version*> .|
|`Language`|facoltativo. Lingua di un assembly localizzato. Il valore predefinito è `neutral`.|
|`ProcessorArchitecture`|facoltativo. Processore del computer di destinazione di questa installazione. Il valore predefinito è `msil`.|

## <a name="externalcheck"></a>ExternalCheck
 Questo elemento è un elemento figlio facoltativo di `InstallChecks` . Per ogni istanza di `ExternalCheck` , il programma di avvio automatico eseguirà il programma esterno denominato in un processo separato e memorizzerà il codice di uscita nella proprietà indicata da `Property` . `ExternalCheck` è utile per l'implementazione di controlli di dipendenza complessi o quando l'unico modo per verificare l'esistenza di un componente è di crearne un'istanza.

 `ExternalCheck` non contiene elementi e ha gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`Property`|Obbligatorio. Nome della proprietà in cui archiviare il risultato. È possibile fare riferimento a questa proprietà da un test sotto l' `InstallConditions` elemento, che è figlio dell' `Command` elemento. Per ulteriori informazioni, vedere [ \<Commands> elemento](../deployment/commands-element-bootstrapper.md).|
|`PackageFile`|Obbligatorio. Programma esterno da eseguire. È necessario che il programma faccia parte del pacchetto di distribuzione del programma di installazione.|
|`Arguments`|facoltativo. Fornisce argomenti della riga di comando al file eseguibile denominato da `PackageFile` .|

## <a name="filecheck"></a>FileCheck
 Questo elemento è un elemento figlio facoltativo di `InstallChecks` . Per ogni istanza di `FileCheck` , il programma di avvio automatico determinerà se il file specificato esiste e restituisce il numero di versione del file. Se il file non dispone di un numero di versione, il programma di avvio automatico imposta la proprietà denominata da `Property` su 0. Se il file non esiste, `Property` non è impostato su alcun valore.

 `FileCheck` non contiene elementi e ha gli attributi seguenti.

| Attributo | Descrizione |
|-----------------| - |
| `Property` | Obbligatorio. Nome della proprietà in cui archiviare il risultato. È possibile fare riferimento a questa proprietà da un test sotto l' `InstallConditions` elemento, che è figlio dell' `Command` elemento. Per ulteriori informazioni, vedere [ \<Commands> elemento](../deployment/commands-element-bootstrapper.md). |
| `FileName` | Obbligatorio. Nome del file da trovare. |
| `SearchPath` | Obbligatorio. Disco o cartella in cui cercare il file. Deve essere un percorso relativo se `SpecialFolder` è assegnato; in caso contrario, deve essere un percorso assoluto. |
| `SpecialFolder` | facoltativo. Cartella che ha un significato speciale a Windows o a [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Il valore predefinito consiste nell'interpretare `SearchPath` come un percorso assoluto. I valori validi sono i seguenti:<br /><br /> `AppDataFolder`. Cartella dei dati dell'applicazione per l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione, specifica dell'utente corrente.<br /><br /> `CommonAppDataFolder`. Cartella Application Data utilizzata da tutti gli utenti.<br /><br /> `CommonFilesFolder`. Cartella dei file comuni per l'utente corrente.<br /><br /> `LocalDataAppFolder`. Cartella dei dati per le applicazioni non in roaming.<br /><br /> `ProgramFilesFolder`. Cartella dei file di programma standard per le applicazioni a 32 bit.<br /><br /> `StartUpFolder`. Cartella che contiene tutte le applicazioni avviate all'avvio del sistema.<br /><br /> `SystemFolder`. Cartella che contiene le DLL di sistema a 32 bit.<br /><br /> `WindowsFolder`. Cartella che contiene l'installazione di sistema di Windows.<br /><br /> `WindowsVolume`. Unità o partizione che contiene l'installazione di sistema di Windows. |
| `SearchDepth` | facoltativo. Profondità in corrispondenza della quale ricercare le sottocartelle per il file specificato. La ricerca è di primo livello. Il valore predefinito è 0, che limita la ricerca alla cartella di livello superiore specificata da `SpecialFolder` e **SearchPath**. |

## <a name="msiproductcheck"></a>MsiProductCheck
 Questo elemento è un elemento figlio facoltativo di `InstallChecks` . Per ogni istanza di `MsiProductCheck` , il programma di avvio automatico verifica se l'installazione Microsoft Windows Installer specificata è stata eseguita fino al completamento. Il valore della proprietà viene impostato in base allo stato del prodotto installato. Un valore positivo indica che il prodotto è installato, 0 o-1 indica che non è installato. Per ulteriori informazioni, vedere la funzione Windows Installer SDK MsiQueryFeatureState. . Se Windows Installer non è installato nel computer, `Property` non è impostato.

 `MsiProductCheck` non contiene elementi e ha gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`Property`|Obbligatorio. Nome della proprietà in cui archiviare il risultato. È possibile fare riferimento a questa proprietà da un test sotto l' `InstallConditions` elemento, che è figlio dell' `Command` elemento. Per ulteriori informazioni, vedere [ \<Commands> elemento](../deployment/commands-element-bootstrapper.md).|
|`Product`|Obbligatorio. GUID del prodotto installato.|
|`Feature`|facoltativo. GUID per una funzionalità specifica dell'applicazione installata.|

## <a name="registrycheck"></a>RegistryCheck
 Questo elemento è un elemento figlio facoltativo di `InstallChecks` . Per ogni istanza di `RegistryCheck` , il programma di avvio automatico verifica se la chiave del registro di sistema specificata esiste o se ha il valore indicato.

 `RegistryCheck` non contiene elementi e ha gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`Property`|Obbligatorio. Nome della proprietà in cui archiviare il risultato. È possibile fare riferimento a questa proprietà da un test sotto l' `InstallConditions` elemento, che è figlio dell' `Command` elemento. Per ulteriori informazioni, vedere [ \<Commands> elemento](../deployment/commands-element-bootstrapper.md).|
|`Key`|Obbligatorio. Nome della chiave del Registro di sistema.|
|`Value`|facoltativo. Nome del valore del registro di sistema da recuperare. Per impostazione predefinita, viene restituito il testo del valore predefinito. `Value` deve essere una stringa o un valore DWORD.|

## <a name="registryfilecheck"></a>RegistryFileCheck
 Questo elemento è un elemento figlio facoltativo di `InstallChecks` . Per ogni istanza di `RegistryFileCheck` , il programma di avvio automatico recupera la versione del file specificato, tentando innanzitutto di recuperare il percorso del file dalla chiave del registro di sistema specificata. Questa operazione è particolarmente utile se si desidera cercare un file in una directory specificata come valore nel registro di sistema.

 `RegistryFileCheck` non contiene elementi e ha gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`Property`|Obbligatorio. Nome della proprietà in cui archiviare il risultato. È possibile fare riferimento a questa proprietà da un test sotto l' `InstallConditions` elemento, che è figlio dell' `Command` elemento. Per ulteriori informazioni, vedere [ \<Commands> elemento](../deployment/commands-element-bootstrapper.md).|
|`Key`|Obbligatorio. Nome della chiave del Registro di sistema. Il valore viene interpretato come il percorso di un file, a meno che non `File` sia impostato l'attributo. Se questa chiave non esiste, `Property` non è impostato.|
|`Value`|facoltativo. Nome del valore del registro di sistema da recuperare. Per impostazione predefinita, viene restituito il testo del valore predefinito. `Value` deve essere una stringa.|
|`FileName`|facoltativo. Nome di un file. Se specificato, il valore ottenuto dalla chiave del registro di sistema viene considerato un percorso di directory e tale nome viene aggiunto al nome. Se non specificato, il valore restituito dal registro di sistema si presuppone che corrisponda al percorso completo di un file.|
|`SearchDepth`|facoltativo. Profondità in corrispondenza della quale ricercare le sottocartelle per il file specificato. La ricerca è di primo livello. Il valore predefinito è 0, che limita la ricerca alla cartella di livello superiore specificata dal valore della chiave del registro di sistema.|

## <a name="remarks"></a>Osservazioni
 Mentre gli elementi sottostanti `InstallChecks` definiscono i test da eseguire, non li eseguono. Per eseguire i test, è necessario creare `Command` elementi sotto l' `Commands` elemento.

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato l' `InstallChecks` elemento usato nel file di prodotto per la .NET Framework.

```xml
<InstallChecks>
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />
</InstallChecks>
```

## <a name="installconditions"></a>InstallConditions
 Quando `InstallChecks` vengono valutati, producono proprietà. Le proprietà vengono quindi utilizzate da `InstallConditions` per determinare se un pacchetto deve eseguire l'installazione, il bypass o l'esito negativo. Nella tabella seguente sono elencate le `InstallConditions` :

|Condizione|Description|
|-|-|
|`FailIf`|Se una `FailIf` condizione restituisce true, il pacchetto avrà esito negativo. Le altre condizioni non verranno valutate.|
|`BypassIf`|Se una `BypassIf` condizione restituisce true, il pacchetto verrà ignorato. Le altre condizioni non verranno valutate.|

## <a name="predefined-properties"></a>Proprietà predefinite
 Nella tabella seguente sono elencati `BypassIf` gli `FailIf` elementi e:

|Proprietà|Note|Valori possibili|
|--------------|-----------|---------------------|
|`Version9X`|Numero di versione di un sistema operativo Windows 9X.|4.10 = Windows 98|
|`VersionNT`|Numero di versione di un sistema operativo basato su Windows NT.|Major.Minor.ServicePack<br /><br /> 5,0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professional SP2<br /><br /> 5.2.0 = Windows Server 2003|
|`VersionNT64`|Numero di versione di un sistema operativo basato su Windows NT a 64 bit.|Come indicato in precedenza.|
|`VersionMsi`|Numero di versione del servizio Windows Installer.|2.0 = Windows Installer 2.0|
|`AdminUser`|Specifica se un utente dispone di privilegi di amministratore in un sistema operativo basato su Windows NT.|0 = nessun privilegio di amministratore<br /><br /> 1 = privilegi di amministratore|

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
>L' `BeforeInstallChecks` attributo è supportato a partire dalla versione di Visual Studio 2019 Update 9.

## <a name="see-also"></a>Vedere anche
- [\<Commands> elemento](../deployment/commands-element-bootstrapper.md)
- [Riferimento allo schema del prodotto e del pacchetto](../deployment/product-and-package-schema-reference.md)