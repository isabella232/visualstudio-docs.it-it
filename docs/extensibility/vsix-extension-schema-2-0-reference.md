---
title: Riferimento allo schema di estensione VSIX 2.0 Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78e260c62d67afc10fea25d52169c48b64c82f72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697919"
---
# <a name="vsix-extension-schema-20-reference"></a>Riferimento allo schema di estensione VSIX 2.0
Un file manifesto di distribuzione VSIX descrive il contenuto di un pacchetto VSIX. Il formato del file è regolato da uno schema. La versione 2.0 di questo schema supporta l'aggiunta di tipi e attributi personalizzati.  Lo schema del manifesto è estensibile. Il caricatore del manifesto ignora gli elementi e gli attributi XML che non riconosce.

> [!IMPORTANT]
> Visual Studio 2015 può caricare file VSIX nei formati di Visual Studio 2010, Visual Studio 2012 o Visual Studio 2013.

## <a name="package-manifest-schema"></a>Schema del manifesto del pacchettoPackage manifest schema
 L'elemento radice del file `<PackageManifest>`XML manifesto è . Ha un singolo `Version`attributo , ovvero la versione del formato del manifesto. Se vengono apportate modifiche importanti al formato, il formato della versione viene modificato. In questo articolo viene descritto il formato del manifesto versione `Version` 2.0, che viene specificato nel manifesto impostando l'attributo sul valore di Version "2.0".

### <a name="packagemanifest-element"></a>Elemento PackageManifest
 All'interno dell'elemento `<PackageManifest>` radice, è possibile utilizzare i seguenti elementi:

- `<Metadata>`- Metadati e informazioni pubblicitarie sul pacchetto stesso. Nel `Metadata` manifesto è consentito un solo elemento.

- `<Installation>`- Questa sezione definisce il modo in cui questo pacchetto di estensione può essere installato, inclusi gli SKU dell'applicazione in cui può essere installato.- This section defines the way this extension package can be installed, including the application SKUs that it can install into. Nel manifesto `Installation` è consentito un solo elemento. Un manifesto deve `Installation` avere un elemento, altrimenti il pacchetto non verrà installato in alcun SKU.

- `<Dependencies>`- Un elenco facoltativo di dipendenze per questo pacchetto è definito qui.- An optional list of dependencies for this package are defined here.

- `<Assets>`- Questa sezione contiene tutti i beni contenuti all'interno di questo pacchetto. Senza questa sezione, questo pacchetto non verrà visualizzata alcun contenuto.

- `<AnyElement>*`- Lo schema del manifesto è sufficientemente flessibile da consentire qualsiasi altro elemento.- The manifest schema is flexible enough to allow any other elements. Tutti gli elementi figlio non riconosciuti dal caricatore del manifesto vengono esposti nell'API di Gestione estensioni come oggetti XmlElement aggiuntivi. Usando questi elementi figlio, le estensioni VSIX possono definire dati aggiuntivi nel file manifesto a cui il codice in esecuzione in Visual Studio può accedere in fase di esecuzione. Vedere [Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120)).

### <a name="metadata-element"></a>Elemento di metadati
 Questa sezione è i metadati relativi al pacchetto, alla sua identità e alle informazioni pubblicitarie. `<Metadata>`contiene i seguenti elementi:

- `<Identity>`- Definisce le informazioni di identificazione per questo pacchetto e include i seguenti attributi:

  - `Id`- Questo attributo deve essere un ID univoco per il pacchetto scelto dall'autore. Il nome deve essere qualificato nello stesso modo in cui i tipi CLR sono con spazio dei nomi: Company.Product.Feature.Name. L'attributo `Id` è limitato a 100 caratteri.

  - `Version`- Definisce la versione di questo pacchetto e il relativo contenuto. Questo attributo segue il formato di controllo delle versioni dell'assembly CLR: Major.Minor.Build.Revision (1.2.40308.00). Un pacchetto con un numero di versione superiore viene considerato aggiornamenti del pacchetto e può essere installato sulla versione installata esistente.

  - `Language`- Questo attributo è la lingua predefinita per il pacchetto e corrisponde ai dati testuali in questo manifesto. Questo attributo segue la convenzione del codice delle impostazioni locali CLR per gli assembly di risorse, ad esempio: en-us, en, fr-fr. È possibile `neutral` specificare di dichiarare un'estensione indipendente dalla lingua che verrà eseguita in qualsiasi versione di Visual Studio.You can specify to declare a language-neutral extension that will run on any version of Visual Studio. Il valore predefinito è `neutral`.

  - `Publisher`- Questo attributo identifica l'autore di questo pacchetto, un nome di società o individuale. L'attributo `Publisher` è limitato a 100 caratteri.

- `<DisplayName>`- Questo elemento specifica il nome descrittivo del pacchetto visualizzato nell'interfaccia utente di Gestione estensioni.- This element specifies the user-friendly package name that is displayed in the Extension Manager UI. Il `DisplayName` contenuto è limitato a 50 caratteri.

- `<Description>`- Questo elemento facoltativo è una breve descrizione del pacchetto e del relativo contenuto visualizzato nell'interfaccia utente di Gestione estensioni.- This optional element is a short description of the package and its contents that is displayed in Extension Manager UI. Il `Description` contenuto può contenere qualsiasi testo desiderato, ma è limitato a 1000 caratteri.

- `<MoreInfo>`- Questo elemento facoltativo è un URL di una pagina online che contiene una descrizione completa di questo pacchetto. Il protocollo deve essere specificato come http.

- `<License>`- Questo elemento facoltativo è un percorso relativo a un file di licenza (.txt, .rtf) contenuto nel pacchetto.

- `<ReleaseNotes>`- Questo elemento facoltativo è un percorso relativo a un file di note sulla versione contenuto nel pacchetto (.txt, .rtf) o un URL di un sito Web che visualizza le note sulla versione.

- `<Icon>`- Questo elemento facoltativo è un percorso relativo a un file di immagine (png, bmp, jpeg, ico) contenuto nel pacchetto.- This optional element is a relative path to an image file (png, bmp, jpeg, ico) contained in the package. L'immagine dell'icona deve essere 32x32 pixel (o verrà ridotto a tale dimensione) e viene visualizzata nell'interfaccia utente di listview. Se `Icon` non viene specificato alcun elemento, l'interfaccia utente utilizza un valore predefinito.

- `<PreviewImage>`- Questo elemento facoltativo è un percorso relativo a un file di immagine (png, bmp, jpeg) contenuto nel pacchetto. L'immagine di anteprima deve essere di 200x200 pixel e visualizzata nell'interfaccia utente dei dettagli. Se `PreviewImage` non viene specificato alcun elemento, l'interfaccia utente utilizza un valore predefinito.

- `<Tags>`- Questo elemento facoltativo elenca i tag di testo delimitati da punti e virgola aggiuntivi utilizzati per gli hint di ricerca. L'elemento `Tags` è limitato a 100 caratteri.

- `<GettingStartedGuide>`- Questo elemento facoltativo è un percorso relativo a un file HTML o un URL a un sito Web che contiene informazioni su come utilizzare l'estensione o il contenuto all'interno di questo pacchetto. Questa guida viene avviata come parte di un'installazione.

- `<AnyElement>*`- Lo schema del manifesto è sufficientemente flessibile da consentire qualsiasi altro elemento.- The manifest schema is flexible enough to allow any other elements. Tutti gli elementi figlio non riconosciuti dal caricatore del manifesto vengono esposti come un elenco di oggetti XmlElement. Usando questi elementi figlio, le estensioni VSIX possono definire dati aggiuntivi nel file manifesto ed enumerarli in fase di esecuzione.

### <a name="installation-element"></a>Elemento di installazione
 Questa sezione definisce il modo in cui questo pacchetto può essere installato e gli SKU dell'applicazione in cui può essere installato. Questa sezione contiene i seguenti attributi:

- `Experimental`- Impostare questo attributo su true se si dispone di un'estensione attualmente installata per tutti gli utenti, ma si sta sviluppando una versione aggiornata nello stesso computer. Ad esempio, se è stato installato MyExtension 1.0 per tutti gli utenti, ma si desidera eseguire il debug di MyExtension 2.0 nello stesso computer, impostare Experimental , "true". Questo attributo è disponibile in Visual Studio 2015 Update 1 e versioni successive.

- `Scope`- Questo attributo può assumere il valore "Global" o "ProductExtension":

  - "Globale" specifica che l'installazione non ha come ambito uno SKU specifico. Ad esempio, questo valore viene utilizzato quando viene installato un SDK di estensione.

  - "ProductExtension" specifica che è installata un'estensione VSIX tradizionale (versione 1.0) con ambito a singoli SKU di Visual Studio."ProductExtension" specifies that a traditional VSIX Extension (version 1.0) scoped to individual Visual Studio SKUsis. Si tratta del valore predefinito.

- `AllUsers`- Questo attributo facoltativo specifica se questo pacchetto verrà installato per tutti gli utenti.- This optional attribute specifies whether this package will be installed for all users. Per impostazione predefinita, questo attributo è false, che specifica che il pacchetto è per utente. (Quando si imposta questo valore su true, l'utente che esegue l'installazione deve elevare al livello di privilegi amministrativi per installare il codice VSIX risultante.

- `InstalledByMsi`- Questo attributo facoltativo specifica se questo pacchetto è installato da un file MSI. I pacchetti installati da un file MSI vengono installati e gestiti da MSI (Programmi e funzionalità) e non da Gestione estensioni di Visual Studio.  Per impostazione predefinita, questo attributo è false, che specifica che il pacchetto non viene installato da un file MSI.

- `SystemComponent`- Questo attributo facoltativo specifica se questo pacchetto deve essere considerato un componente di sistema.- This optional attribute specifies whether this package should be considered a system component. I componenti di sistema non vengono visualizzati nell'interfaccia utente di Gestione estensioni e non possono essere aggiornati. Per impostazione predefinita, questo attributo è false, che specifica che il pacchetto non è un componente di sistema.

- `AnyAttribute*`- `Installation` L'elemento accetta un set aperto di attributi che verranno esposti in fase di esecuzione come dizionario di coppie nome-valore.- The element accepts an open-ended set of attributes that will be exposed at run time as a name-value pair dictionary.

- `<InstallationTarget>`-Questo elemento controlla il percorso in cui il programma di installazione VSIX installa il pacchetto.-This element controls the location where the VSIX installer installs the package. Se il valore `Scope` dell'attributo è "ProductExtension", il pacchetto deve essere destinato a uno SKU, che ha installato un file manifesto come parte del contenuto per annunciare la disponibilità alle estensioni. L'elemento `<InstallationTarget>` ha i `Scope` seguenti attributi quando l'attributo ha il valore esplicito o predefinito "ProductExtension":

  - `Id`- Questo attributo identifica il pacchetto.  L'attributo segue la convenzione dello spazio dei nomi: Company.Product.Feature.Name. L'attributo `Id` può contenere solo caratteri alfanumerici ed è limitato a 100 caratteri. Valori previsti:

    - Microsoft.VisualStudio.IntegratedShell

    - Microsoft.VisualStudio.Pro

    - Microsoft.VisualStudio.Premium

    - Microsoft.VisualStudio.Ultimate

    - Microsoft.VisualStudio.VWDExpress

    - Microsoft.VisualStudio.VPDExpress

    - Microsoft.VisualStudio.VSWinExpress

    - Microsoft.VisualStudio.VSLS

    - My.Shell.App

  - `Version`- Questo attributo specifica un intervallo di versioni con le versioni supportate minima e massima di questo SKU. Un pacchetto può descrivere in dettaglio le versioni degli SKU che supporta. La notazione dell'intervallo di versioni è [10.0 - 11.0], dove

    - [ - versione minima inclusa.

    - ] - versione massima inclusa.

    - ( - versione minima esclusiva.

    - ) - versione massima esclusiva.

    - Versione singola: solo la versione specificata.

    > [!IMPORTANT]
    > La versione 2.0 dello schema VSIX è stata introdotta in Visual Studio 2012. Per utilizzare questo schema è necessario disporre di Visual Studio 2012 o versione successiva installato nel computer e utilizzare VSIXInstaller.exe che fa parte di tale prodotto. È possibile scegliere come destinazione le versioni precedenti di Visual Studio con un VSIXInstaller di Visual Studio 2012 o versione successiva, ma solo utilizzando le versioni successive del programma di installazione.

    I numeri di versione di Visual Studio 2017 sono disponibili in Numeri di build e date di rilascio di [Visual Studio.](../install/visual-studio-build-numbers-and-release-dates.md)

    Quando si esprime la versione per le versioni di Visual Studio 2017, la versione secondaria deve essere sempre **0**. Ad esempio, Visual Studio 2017 versione 15.3.26730.0 deve essere espresso come [15.0.26730.0,16.0). Questa operazione è necessaria solo per Visual Studio 2017 e i numeri di versione successivi.

  - `AnyAttribute*`- `<InstallationTarget>` L'elemento consente un set aperto di attributi esposto in fase di esecuzione come dizionario di coppie nome-valore.- The element allows an open-ended set of attributes that is exposed at run time as a name-value pair dictionary.

### <a name="dependencies-element"></a>Elemento Dipendenzs
 Questo elemento contiene un elenco di dipendenze dichiarate da questo pacchetto. Se vengono specificate dipendenze, tali `Id`pacchetti (identificati dal relativo ) devono essere stati installati in precedenza.

- `<Dependency>`element - Questo elemento figlio ha i seguenti attributi:

  - `Id`- Questo attributo deve essere un ID univoco per il pacchetto dipendente. Questo valore di `<Metadata><Identity>Id` identità deve corrispondere all'attributo di un pacchetto da cui dipende questo pacchetto. L'attributo `Id` segue la convenzione dello spazio dei nomi: Company.Product.Feature.Name. L'attributo può contenere solo caratteri alfanumerici ed è limitato a 100 caratteri.

  - `Version`- Questo attributo specifica un intervallo di versioni con le versioni supportate minima e massima di questo SKU. Un pacchetto può descrivere in dettaglio le versioni degli SKU che supporta. La notazione dell'intervallo di versioni è [12.0, 13.0], dove:

    - [ - versione minima inclusa.

    - ] - versione massima inclusa.

    - ( - versione minima esclusiva.

    - ) - versione massima esclusiva.

    - Versione singola: solo la versione specificata.

  - `DisplayName`- Questo attributo è il nome visualizzato del pacchetto dipendente, che viene utilizzato negli elementi dell'interfaccia utente, ad esempio finestre di dialogo e messaggi di errore. L'attributo è facoltativo a meno che il pacchetto dipendente non sia installato da MSI.

  - `Location`- Questo attributo facoltativo specifica il percorso relativo all'interno di questo valore VSIX a un pacchetto VSIX annidato o un URL al percorso di download per la dipendenza.- This optional attribute specifies either the relative path within this VSIX to a nested VSIX package or a URL to the download location for the dependency. Questo attributo viene utilizzato per consentire all'utente di individuare il pacchetto dei prerequisiti.

  - `AnyAttribute*`- `Dependency` L'elemento accetta un set aperto di attributi che verranno esposti in fase di esecuzione come dizionario di coppie nome-valore.- The element accepts an open-ended set of attributes that will be exposed at run time as a name-value pair dictionary.

### <a name="assets-element"></a>Elemento Assets
 Questo elemento contiene `<Asset>` un elenco di tag per ogni estensione o elemento di contenuto visualizzato da questo pacchetto.

- `<Asset>`- Questo elemento contiene i seguenti attributi ed elementi:

  - `Type`- Tipo di estensione o contenuto rappresentato da questo elemento. Ogni `<Asset>` elemento deve `Type`avere un `<Asset>` singolo elemento `Type`, ma più elementi possono avere lo stesso . Questo attributo deve essere rappresentato come nome completo, in base alle convenzioni dello spazio dei nomi. I tipi noti sono:

    1. Microsoft.VisualStudio.VsPackage

    2. Microsoft.VisualStudio.MefComponent

    3. Microsoft.VisualStudio.ToolboxControl

    4. Microsoft.VisualStudio.Samples

    5. Microsoft.VisualStudio.ProjectTemplate

    6. Microsoft.VisualStudio.ItemTemplate

    7. Microsoft.VisualStudio.Assembly

       È possibile creare tipi personalizzati e assegnare loro nomi univoci. In fase di esecuzione all'interno di Visual Studio, il codice può enumerare e accedere a questi tipi personalizzati tramite l'API di Gestione estensioni.

  - `Path`- il percorso relativo al file o alla cartella all'interno del pacchetto che contiene l'asset.

  - `TargetVersion`- l'intervallo di versione a cui si applica l'asset specificato. Utilizzato per la distribuzione di più versioni di risorse a versioni diverse di Visual Studio. Richiede Visual Studio 2017.3 o più recente per avere effetto.

  - `AnyAttribute*`- Un set aperto di attributi esposto in fase di esecuzione come dizionario di coppie nome-valore.

    `<AnyElement>*`- Qualsiasi contenuto strutturato `<Asset>` è consentito tra un tag di inizio e di fine. Tutti gli elementi vengono esposti come un elenco di XmlElement oggetti. Le estensioni VSIX possono definire metadati strutturati specifici del tipo nel file manifesto ed enumerarli in fase di esecuzione.

### <a name="sample-manifest"></a>Manifesto di esempio

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
  <Metadata>
    <Identity Id="0000000-0000-0000-0000-000000000000" Version="1.0" Language="en-US" Publisher="Company" />
    <DisplayName>Test Package</DisplayName>
    <Description>Information about my package</Description>
    <MoreInfo>http://www.fabrikam.com/Extension1/</MoreInfo>
    <License>eula.rtf</License>
    <ReleaseNotes>notes.txt</ReleaseNotes>
    <Icon>Images\icon.png</Icon>
    <PreviewImage>Images\preview.png</PreviewImage>
  </Metadata>
  <Installation InstalledByMsi="false" AllUsers="false" SystemComponent="false" Scope="ProductExtension">
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="[11.0, 12.0]" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="[4.5,)" />
    <Dependency Id="Microsoft.VisualStudio.MPF.12.0" DisplayName="Visual Studio MPF 12.0" d:Source="Installed" Version="[12.0]" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.VsPackage" d:Source="Project" d:ProjectName="%CurrentProject%" Path="|%CurrentProject%;PkgdefProjectOutputGroup|" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>Vedere anche

- [Spedire le estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
