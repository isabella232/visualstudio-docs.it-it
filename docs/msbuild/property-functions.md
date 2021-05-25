---
title: Funzioni di proprietà | Microsoft Docs
description: Informazioni su come usare le funzioni di proprietà, che sono chiamate .NET Framework metodi che vengono visualizzati nelle definizioni di proprietà di MSBuild.
ms.custom: SEO-VS-2020
ms.date: 02/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7c4a6254f15a4108c525231d0e5e93c6fc71bfb3
ms.sourcegitcommit: d3577395cf016f2836eb5a3c1d496cca6d449baa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/25/2021
ms.locfileid: "110413338"
---
# <a name="property-functions"></a>Funzioni delle proprietà

Le funzioni di proprietà sono chiamate .NET Framework metodi che vengono visualizzati nelle definizioni di proprietà di MSBuild. A differenza delle attività, le funzioni di proprietà possono essere usate all'esterno delle destinazioni e vengono valutate prima dell'esecuzione delle destinazioni.

Senza usare le attività MSBuild, è possibile leggere l'ora di sistema, confrontare stringhe, trovare la corrispondenza per espressioni regolari ed eseguire altre azioni nello script di compilazione. MSBuild tenterà di convertire le stringhe in numeri e i numeri in stringhe nonché di eseguire altre conversioni secondo le esigenze.

Nei valori stringa restituiti da funzioni di proprietà i [caratteri speciali](msbuild-special-characters.md) sono sottoposti a escape. Se si vuole che il valore venga trattato come se fosse stato inserito direttamente nel file di progetto, usare `$([MSBuild]::Unescape())` per rimuovere gli escape dai caratteri speciali.

Le funzioni di proprietà sono disponibili con .NET Framework 4 e versioni successive.

## <a name="property-function-syntax"></a>Sintassi delle funzioni di proprietà

Di seguito sono elencati tre tipi di funzioni di proprietà. Ogni funzione presenta una sintassi diversa:

- Funzioni di proprietà stringa (istanza)
- Funzioni di proprietà statiche
- Funzioni di proprietà MSBuild

### <a name="string-property-functions"></a>Funzioni di proprietà stringa

Tutti i valori delle proprietà di compilazione sono soltanto valori stringa. Per agire su qualsiasi valore di proprietà è possibile usare i metodi stringa (istanza). Ad esempio, è possibile estrarre il nome di unità, ovvero i primi tre caratteri, da una proprietà di compilazione che rappresenta un percorso completo con questo codice:

```
$(ProjectOutputFolder.Substring(0,3))
```

### <a name="static-property-functions"></a>Funzioni di proprietà statiche

Nello script di compilazione è possibile accedere alle proprietà e ai metodi statici di molte classi di sistema. Per ottenere il valore di una proprietà statica, usare la sintassi seguente, dove è il nome della classe di sistema e \<Class> è il nome della \<Property> proprietà.

```
$([Class]::Property)
```

Ad esempio, è possibile usare il codice seguente per impostare una proprietà di compilazione sulla data e sull'ora correnti.

```xml
<Today>$([System.DateTime]::Now)</Today>
```

Per chiamare un metodo statico, usare la sintassi seguente, dove è il nome della classe di sistema, è il nome del metodo e ( ) è l'elenco di parametri \<Class> \<Method> per il \<Parameters> metodo:

```
$([Class]::Method(Parameters))
```

Ad esempio per impostare una proprietà di compilazione su un nuovo GUID, è possibile usare lo script seguente:

```xml
<NewGuid>$([System.Guid]::NewGuid())</NewGuid>
```

Nelle funzioni di proprietà statiche è possibile usare qualsiasi proprietà o metodo statico delle classi di sistema seguenti:

- <xref:System.Byte?displayProperty=nameWithType>
- <xref:System.Char?displayProperty=nameWithType>
- <xref:System.Convert?displayProperty=nameWithType>
- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Enum?displayProperty=nameWithType>
- <xref:System.Guid?displayProperty=nameWithType>
- <xref:System.Int16?displayProperty=nameWithType>
- <xref:System.Int32?displayProperty=nameWithType>
- <xref:System.Int64?displayProperty=nameWithType>
- <xref:System.IO.Path?displayProperty=nameWithType>
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.OSPlatform?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation?displayProperty=nameWithType>
- <xref:System.UInt16?displayProperty=nameWithType>
- <xref:System.UInt32?displayProperty=nameWithType>
- <xref:System.UInt64?displayProperty=nameWithType>
- <xref:System.SByte?displayProperty=nameWithType>
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.StringComparer?displayProperty=nameWithType>
- <xref:System.TimeSpan?displayProperty=nameWithType>
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- <xref:System.UriBuilder?displayProperty=nameWithType>
- <xref:System.Version?displayProperty=nameWithType>
- <xref:Microsoft.Build.Utilities.ToolLocationHelper?displayProperty=nameWithType>

Inoltre, è possibile usare le proprietà e i metodi statici seguenti:

- [System.Environment::CommandLine](xref:System.Environment.CommandLine*)
- [System.Environment::ExpandEnvironmentVariables](xref:System.Environment.ExpandEnvironmentVariables*)
- [System.Environment::GetEnvironmentVariable](xref:System.Environment.GetEnvironmentVariable*)
- [System.Environment::GetEnvironmentVariables](xref:System.Environment.GetEnvironmentVariables*)
- [System.Environment::GetFolderPath](xref:System.Environment.GetFolderPath*)
- [System.Environment::GetLogicalDrives](xref:System.Environment.GetLogicalDrives*)
- [System.IO.Directory::GetDirectories](xref:System.IO.Directory.GetDirectories*)
- [System.IO.Directory::GetFiles](xref:System.IO.Directory.GetFiles*)
- [System.IO.Directory::GetLastAccessTime](xref:System.IO.Directory.GetLastAccessTime*)
- [System.IO.Directory::GetLastWriteTime](xref:System.IO.Directory.GetLastWriteTime*)
- [System.IO.Directory::GetParent](xref:System.IO.Directory.GetParent*)
- [System.IO.File::Exists](xref:System.IO.File.Exists*)
- [System.IO.File::GetCreationTime](xref:System.IO.File.GetCreationTime*)
- [System.IO.File::GetAttributes](xref:System.IO.File.GetAttributes*)
- [System.IO.File::GetLastAccessTime](xref:System.IO.File.GetLastAccessTime*)
- [System.IO.File::GetLastWriteTime](xref:System.IO.File.GetLastWriteTime*)
- [System.IO.File::ReadAllText](xref:System.IO.File.ReadAllText*)

### <a name="calling-instance-methods-on-static-properties"></a>Chiamata di metodi di istanza su proprietà statiche

Se si accede a una proprietà statica che restituisce un'istanza di un oggetto, è possibile richiamare i metodi di istanza di tale oggetto. Per richiamare un metodo di istanza, usare la sintassi seguente, dove è il nome della classe di sistema, è il nome della proprietà, è il nome del metodo e ( ) è l'elenco di parametri per \<Class> \<Property> il \<Method> \<Parameters> metodo:

```
$([Class]::Property.Method(Parameters))
```

Il nome della classe deve essere completo con lo spazio dei nomi.

Ad esempio, è possibile usare il codice seguente per impostare una proprietà di compilazione sulla data corrente.

```xml
<Today>$([System.DateTime]::Now.ToString('yyyy.MM.dd'))</Today>
```

### <a name="msbuild-property-functions"></a>Funzioni di proprietà MSBuild

È possibile accedere a diversi metodi statici nella compilazione per supportare funzionalità aritmetiche, operazioni logiche bit per bit nonché la gestione dei caratteri di escape. È possibile accedere a questi metodi usando la sintassi seguente, dove è il nome del metodo e ( ) è l'elenco \<Method> di parametri per il \<Parameters> metodo.

```
$([MSBuild]::Method(Parameters))
```

Ad esempio, per sommare due proprietà che presentano valori numerici, usare il codice seguente.

```
$([MSBuild]::Add($(NumberOne), $(NumberTwo)))
```

Di seguito è riportato un elenco di funzioni di proprietà MSBuild:

|Firma della funzione|Descrizione|
|------------------------|-----------------|
|double Add(double a, double b)|Esegue l'addizione di due valori Double.|
|long Add(long a, long b)|Esegue l'addizione di due valori Long.|
|double Subtract(double a, double b)|Esegue la sottrazione tra due valori Double.|
|long Subtract(long a, long b)|Esegue la sottrazione tra due valori Long.|
|double Multiply(double a, double b)|Esegue la moltiplicazione tra due valori Double.|
|long Multiply(long a, long b)|Esegue la moltiplicazione tra due valori Long.|
|double Divide(double a, double b)|Esegue la divisione tra due valori Double.|
|long Divide(long a, long b)|Esegue la divisione tra due valori Long.|
|double Modulo(double a, double b)|Esegue l'operazione modulo tra due valori Double.|
|long Modulo(long a, long b)|Esegue l'operazione modulo tra due valori Long.|
|string Escape(string unescaped)|Aggiunge i caratteri di escape alla stringa in base alle regole di escape di MSBuild.|
|string Unescape(string escaped)|Rimuove i caratteri di escape dalla stringa in base alle regole di escape di MSBuild.|
|int BitwiseOr(int first, int second)|Esegue un'operazione `OR` bit per bit tra il primo e il secondo valore (primo &#124; secondo).|
|int BitwiseAnd(int first, int second)|Esegue un'operazione `AND` bit per bit tra il primo e il secondo valore (primo & secondo).|
|int BitwiseXor(int first, int second)|Esegue un'operazione `XOR` bit per bit tra il primo e il secondo valore (primo ^ secondo).|
|int BitwiseNot(int first)|Esegue un'operazione `NOT` bit per bit (~primo).|
|bool IsOsPlatform(string platformString)|Specifica se la piattaforma del sistema operativo corrente è `platformString`. `platformString` deve essere membro di <xref:System.Runtime.InteropServices.OSPlatform>.|
|bool IsOSUnixLike()|True se il sistema operativo corrente è un sistema Unix.|
|string NormalizePath(params string[] path)|Ottiene il percorso completo in forma canonica corrispondente al percorso specificato e garantisce che contenga i separatori di directory corretti per il sistema operativo corrente.|
|string NormalizeDirectory(params string[] path)|Ottiene il percorso completo in forma canonica della directory specificata e garantisce che contenga i separatori di directory corretti per il sistema operativo corrente e una barra rovesciata finale.|
|string EnsureTrailingSlash(string path)|Se il percorso specificato non dispone di una barra rovesciata, la aggiunge al percorso. Se il percorso è una stringa vuota non lo modifica.|
|string GetPathOfFileAbove(string file, string startingDirectory)|Cerca e restituisce il percorso completo di un file nella struttura di directory sopra il percorso del file di compilazione corrente o in base a `startingDirectory` , se specificato.|
|GetDirectoryNameOfFileAbove(string startingDirectory, string fileName)|Individuare e restituire la directory di un file nella directory specificata o in un percorso nella struttura di directory al di sopra di tale directory.|
|string MakeRelative(string basePath, string path)|Rende `path` relativo a `basePath`. `basePath` deve essere una directory assoluta. Se `path` non può essere reso relativo, viene restituito letteralmente. Simile a `Uri.MakeRelativeUri`.|
|string ValueOrDefault(string conditionValue, string defaultValue)|Restituisce la stringa nel parametro 'defaultValue' solo se il parametro 'conditionValue' è vuoto. In caso contrario, restituisce il valore conditionValue.|

## <a name="nested-property-functions"></a>Funzioni di proprietà annidate

È possibile combinare le funzioni di proprietà per formare funzioni più complesse, come mostrato nell'esempio seguente.

```
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

Questo esempio restituisce il valore di bit <xref:System.IO.FileAttributes>`Archive` (32 o 0) del file fornito dal percorso `tempFile`. Notare che i valori di dati enumerati non possono essere specificati per nome all'interno delle funzioni di proprietà. È necessario usare invece il valore numerico (32).

Nelle funzioni di proprietà annidate è possibile specificare anche i metadati. Per altre informazioni, vedere [Batch](../msbuild/msbuild-batching.md).

## <a name="msbuild-doestaskhostexist"></a>MSBuild DoesTaskHostExist

La funzione di proprietà `DoesTaskHostExist` in MSBuild restituisce un valore che indica se un host attività è attualmente installato per i valori di architettura e runtime specificati.

Questa funzione di proprietà presenta la seguente sintassi:

```
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>EnsureTrailingSlash di MSBuild

La funzione di proprietà `EnsureTrailingSlash` in MSBuild aggiunge una barra finale se non ne esiste già una.

Questa funzione di proprietà presenta la seguente sintassi:

```
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>MSBuild GetDirectoryNameOfFileAbove

La funzione di proprietà MSBuild `GetDirectoryNameOfFileAbove` cerca un file nelle directory al di sopra della directory corrente nel percorso.

 Questa funzione di proprietà presenta la seguente sintassi:

```
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 Il codice seguente è un esempio di questa sintassi.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>GetPathOfFileAbove di MSBuild

La funzione di proprietà in MSBuild restituisce il percorso del file specificato, se si trova `GetPathOfFileAbove` nella struttura di directory sopra la directory corrente. Dal punto di vista funzionale è equivalente alla chiamata

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

Questa funzione di proprietà presenta la seguente sintassi:

```
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>MSBuild GetRegistryValue

La funzione di proprietà MSBuild `GetRegistryValue` restituisce il valore di una chiave del Registro di sistema. Questa funzione accetta due argomenti, il nome della chiave e il nome del valore e restituisce il valore dal Registro di sistema. Se non si specifica un nome del valore, viene restituito il valore predefinito.

Gli esempi seguenti mostrano come viene usata questa funzione:

```
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>MSBuild GetRegistryValueFromView

La funzione di proprietà MSBuild `GetRegistryValueFromView` ottiene i dati del Registro di sistema in base alla chiave e al valore del Registro di sistema forniti, nonché a una o più visualizzazioni ordinate del Registro di sistema. La chiave e il valore vengono cercati in ogni visualizzazione del Registro di sistema in ordine, finché non vengono trovati.

Di seguito è indicata la sintassi per la funzione della proprietà:

```
[MSBuild]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)
```

Il sistema operativo Windows a 64 bit gestisce una chiave del Registro di sistema **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node** che presenta una visualizzazione del Registro di sistema **HKEY_LOCAL_MACHINE\SOFTWARE** per le applicazioni a 32 bit.

Per impostazione predefinita, un'applicazione a 32 bit in esecuzione su WOW64 accede alla visualizzazione del Registro di sistema a 32 bit e un'applicazione a 64 bit accede alla visualizzazione del Registro di sistema a 64 bit.

Sono disponibili le visualizzazioni del Registro di sistema seguenti:

|Visualizzazione del Registro di sistema|Definizione|
|-------------------|----------------|
|RegistryView.Registry32|Visualizzazione del Registro di sistema dell'applicazione a 32 bit.|
|RegistryView.Registry64|Visualizzazione del Registro di sistema dell'applicazione a 64 bit.|
|RegistryView.Default|Visualizzazione del Registro di sistema che corrisponde al processo su cui è in esecuzione l'applicazione.|

Di seguito è riportato un esempio.

 ```
$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))
```

ottiene i **dati SLRuntimeInstallPath** della chiave **ReferenceAssemblies,** esaminando prima nella visualizzazione del Registro di sistema a 64 bit e quindi nella visualizzazione del Registro di sistema a 32 bit.

## <a name="msbuild-makerelative"></a>MSBuild MakeRelative

La funzione di proprietà MSBuild `MakeRelative` restituisce il percorso relativo del secondo percorso relativo al primo percorso. Ogni percorso può essere un file o una cartella.

Questa funzione di proprietà presenta la seguente sintassi:

```
$([MSBuild]::MakeRelative($(FileOrFolderPath1), $(FileOrFolderPath2)))
```

Il codice seguente è un esempio di questa sintassi.

```xml
<PropertyGroup>
    <Path1>c:\users\</Path1>
    <Path2>c:\users\username\</Path2>
</PropertyGroup>

<Target Name = "Go">
    <Message Text ="$([MSBuild]::MakeRelative($(Path1), $(Path2)))" />
    <Message Text ="$([MSBuild]::MakeRelative($(Path2), $(Path1)))" />
</Target>

<!--
Output:
   username\
   ..\
-->
```

## <a name="msbuild-valueordefault"></a>MSBuild ValueOrDefault

La funzione di proprietà MSBuild `ValueOrDefault` restituisce il primo argomento, a meno che non sia null o vuoto. Se il primo argomento è null o vuoto, la funzione restituisce il secondo argomento.

Gli esempi seguenti mostrano come viene usata questa funzione.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <Value1>$([MSBuild]::ValueOrDefault('$(UndefinedValue)', 'a'))</Value1>
        <Value2>$([MSBuild]::ValueOrDefault('b', '$(Value1)'))</Value2>
    </PropertyGroup>

    <Target Name="MyTarget">
        <Message Text="Value1 = $(Value1)" />
        <Message Text="Value2 = $(Value2)" />
    </Target>
</Project>

<!--
Output:
  Value1 = a
  Value2 = b
-->
```

## <a name="msbuild-targetframework-and-targetplatform-functions"></a>Funzioni TargetFramework e TargetPlatform di MSBuild

MSBuild 16.7 e versioni successive definiscono diverse funzioni per la gestione [delle proprietà TargetFramework e TargetPlatform](msbuild-target-framework-and-target-platform.md).

|Firma della funzione|Descrizione|
|------------------------|-----------------|
|GetTargetFrameworkIdentifier(string targetFramework)|Analizzare TargetFrameworkIdentifier da TargetFramework.|
|GetTargetFrameworkVersion(string targetFramework)|Analizzare TargetFrameworkVersion da TargetFramework.|
|GetTargetPlatformIdentifier(string targetFramework)|Analizzare TargetPlatformIdentifier da TargetFramework.|
|GetTargetPlatformVersion(string targetFramework)|Analizzare TargetPlatformVersion da TargetFramework.|
|IsTargetFrameworkCompatible(string targetFrameworkTarget, string targetFrameworkCandidate)|Restituisce 'True' se il framework di destinazione candidato è compatibile con questo framework di destinazione e false in caso contrario.|

L'esempio seguente illustra come vengono usate queste funzioni. 

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <Value1>$([MSBuild]::GetTargetFrameworkIdentifier('net5.0-windows7.0'))</Value1>
        <Value2>$([MSBuild]::GetTargetFrameworkVersion('net5.0-windows7.0'))</Value2>
        <Value3>$([MSBuild]::GetTargetPlatformIdentifier('net5.0-windows7.0'))</Value3>
        <Value4>$([MSBuild]::GetTargetPlatformVersion('net5.0-windows7.0'))</Value4>
        <Value5>$([MSBuild]::IsTargetFrameworkCompatible('net5.0-windows', 'net5.0'))</Value5>
    </PropertyGroup>

    <Target Name="MyTarget">
        <Message Text="Value1 = $(Value1)" />
        <Message Text="Value2 = $(Value2)" />
        <Message Text="Value3 = $(Value3)" />
        <Message Text="Value4 = $(Value4)" />
        <Message Text="Value5 = $(Value5)" />
    </Target>
</Project>
```

```output
Value1 = .NETCoreApp
Value2 = 5.0
Value3 = windows
Value4 = 7.0
Value5 = True
```

## <a name="msbuild-version-comparison-functions"></a>Funzioni di confronto tra versioni di MSBuild

MSBuild 16.5 e versioni successive definiscono diverse funzioni per confrontare stringhe che rappresentano le versioni.

> [!Note]
> Gli operatori di confronto nelle [condizioni possono confrontare stringhe che possono essere analizzate come `System.Version` oggetti](#msbuild-conditions.md#Comparing-versions), ma il confronto può produrre risultati imprevisti. Preferire le funzioni di proprietà.

|Firma della funzione|Descrizione|
|------------------------|-----------------|
|VersionEquals(string a, string b)|Restituisce `true` se le versioni e sono `a` `b` equivalenti in base alle regole seguenti.|
|VersionGreaterThan(string a, string b)|Restituisce `true` se la versione è maggiore di in base alle regole `a` `b` seguenti.|
|VersionGreaterThanOrEquals(string a, string b)|Restituisce `true` se la versione è maggiore o uguale a in base alle regole `a` `b` seguenti.|
|VersionLessThan(string a, string b)|Restituisce `true` se la versione è minore di in base alle regole `a` `b` seguenti.|
|VersionLessThanOrEquals(string a, string b)|Restituisce `true` se la versione è minore o uguale a in base alle regole `a` `b` seguenti.|
|VersionNotEquals(string a, string b)|Restituisce `false` se le versioni e sono `a` `b` equivalenti in base alle regole seguenti.|

In questi metodi le versioni vengono analizzate come <xref:System.Version?displayProperty=fullName> , con le eccezioni seguenti:

* Il `v` valore iniziale di o viene `V` ignorato, che consente il confronto con `$(TargetFrameworkVersion)` .

* Tutti gli elementi dalla prima "-" o "+" alla fine della stringa di versione vengono ignorati. In questo modo è possibile passare versioni semantiche (semver), anche se l'ordine non è uguale a semver. Al contrario, gli identificatori di versione non definitiva e i metadati di compilazione non hanno alcuno spessore di ordinamento. Può essere utile, ad esempio, per attivare una funzionalità per `>= x.y` e attivarla in `x.y.z-pre` .

* Le parti non specifiche sono uguali a parti con valore zero. (`x == x.0 == x.0.0 == x.0.0.0`).

* Lo spazio vuoto non è consentito nei componenti integer.

* La sola versione principale è valida ( `3` è uguale a `3.0.0.0` )

* `+` non è consentito come segno positivo nei componenti integer (viene considerato come metadati semver e ignorato)

> [!TIP]
> I confronti delle [proprietà TargetFramework devono](msbuild-target-framework-and-target-platform.md) in genere usare [IsTargetFrameworkCompatible](#MSBuild-TargetFramework-and-TargetPlatform-functions) invece di estrarre e confrontare le versioni. Ciò consente il `TargetFramework` confronto di che variano sia in che in `TargetFrameworkIdentifier` versione.

## <a name="msbuild-condition-functions"></a>Funzioni di condizione di MSBuild

Le funzioni `Exists` e non sono funzioni di `HasTrailingSlash` proprietà. Sono disponibili per l'uso con `Condition` l'attributo . Vedere [Condizioni di MSBuild](msbuild-conditions.md).

## <a name="see-also"></a>Vedi anche

- [proprietà di MSBuild](../msbuild/msbuild-properties.md)

- [Panoramica di MSBuild](../msbuild/msbuild.md)
