---
title: Informazioni di riferimento sullo schema dell'estensione VSIX 2.0 | Microsoft Docs
description: Lo schema dell'estensione VSIX 2.0 definisce il formato di file per un file manifesto della distribuzione VSIX, che descrive il contenuto di un pacchetto VSIX.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: baaa03b01e7f211bfc6822e7fcf017d1a49ad324
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158099"
---
# <a name="vsix-extension-schema-20-reference"></a>Informazioni di riferimento sullo schema dell'estensione VSIX 2.0
Un file manifesto della distribuzione VSIX descrive il contenuto di un pacchetto VSIX. Il formato di file è regolato da uno schema. La versione 2.0 di questo schema supporta l'aggiunta di tipi e attributi personalizzati.  Lo schema del manifesto è estendibile. Il caricatore del manifesto ignora gli elementi e gli attributi XML che non è in conoscenza.

> [!IMPORTANT]
> Visual Studio 2015 può caricare file VSIX nei formati Visual Studio 2010, Visual Studio 2012 o Visual Studio 2013.

## <a name="package-manifest-schema"></a>Schema del manifesto del pacchetto
 L'elemento radice del file XML del manifesto è `<PackageManifest>` . Ha un singolo attributo `Version` , che è la versione del formato del manifesto. Se vengono apportate modifiche importanti al formato, il formato della versione viene modificato. Questo articolo descrive la versione 2.0 del formato manifesto, specificata nel manifesto impostando l'attributo sul valore `Version` version="2.0".

### <a name="packagemanifest-element"></a>Elemento PackageManifest
 `<PackageManifest>`All'interno dell'elemento radice è possibile usare gli elementi seguenti:

- `<Metadata>` - Metadati e informazioni pubblicitarie sul pacchetto stesso. Nel manifesto `Metadata` è consentito un solo elemento.

- `<Installation>` - Questa sezione definisce la modalità di installazione di questo pacchetto di estensione, inclusi gli SKU dell'applicazione in cui può essere installato. Nel manifesto `Installation` è consentito un solo elemento. Un manifesto deve avere un elemento . In caso contrario, `Installation` questo pacchetto non verrà installato in alcun SKU.

- `<Dependencies>` - Un elenco facoltativo di dipendenze per questo pacchetto è definito qui.

- `<Assets>` - Questa sezione contiene tutti gli asset contenuti in questo pacchetto. Senza questa sezione, questo pacchetto non presenterà alcun contenuto.

- `<AnyElement>*` - Lo schema del manifesto è sufficientemente flessibile da consentire qualsiasi altro elemento. Tutti gli elementi figlio non riconosciuti dal caricatore del manifesto vengono esposti nell'API di Gestione estensioni come oggetti XmlElement aggiuntivi. Usando questi elementi figlio, le estensioni VSIX possono definire dati aggiuntivi nel file manifesto a cui il codice in Visual Studio può accedere in fase di esecuzione. Vedere [Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements.](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120))

### <a name="metadata-element"></a>Elemento Metadata
 Questa sezione contiene i metadati relativi al pacchetto, alla relativa identità e alle informazioni pubblicitarie. `<Metadata>` contiene gli elementi seguenti:

- `<Identity>` : definisce le informazioni di identificazione per questo pacchetto e include gli attributi seguenti:

  - `Id` - Questo attributo deve essere un ID univoco per il pacchetto scelto dall'autore. Il nome deve essere qualificato nello stesso modo in cui vengono denoti i tipi CLR: Company.Product.Feature.Name. `Id`L'attributo è limitato a 100 caratteri.

  - `Version` : definisce la versione di questo pacchetto e il relativo contenuto. Questo attributo segue il formato di controllo delle versioni degli assembly CLR: Major.Minor.Build.Revision (1.2.40308.00). Un pacchetto con un numero di versione superiore viene considerato come aggiornamenti del pacchetto e può essere installato nella versione installata esistente.

  - `Language` - Questo attributo è la lingua predefinita per il pacchetto e corrisponde ai dati testuali in questo manifesto. Questo attributo segue la convenzione del codice delle impostazioni locali CLR per gli assembly di risorse, ad esempio en-us, en, fr-fr. È possibile specificare `neutral` per dichiarare un'estensione indipendente dal linguaggio che verrà eseguita in qualsiasi versione di Visual Studio. Il valore predefinito è `neutral`.

  - `Publisher` : questo attributo identifica l'editore del pacchetto, una società o un singolo nome. `Publisher`L'attributo è limitato a 100 caratteri.

- `<DisplayName>` : questo elemento specifica il nome descrittivo del pacchetto visualizzato nell'interfaccia utente di Gestione estensioni. Il `DisplayName` contenuto è limitato a 50 caratteri.

- `<Description>` - Questo elemento facoltativo è una breve descrizione del pacchetto e del relativo contenuto visualizzato nell'interfaccia utente di Gestione estensioni. Il `Description` contenuto può contenere qualsiasi testo desiderato, ma è limitato a 1000 caratteri.

- `<MoreInfo>` - Questo elemento facoltativo è un URL di una pagina online che contiene una descrizione completa del pacchetto. Il protocollo deve essere specificato come http.

- `<License>` - Questo elemento facoltativo è un percorso relativo di un file di licenza (.txt, RTF) contenuto nel pacchetto.

- `<ReleaseNotes>` - Questo elemento facoltativo è un percorso relativo di un file delle note sulla versione contenuto nel pacchetto (.txt, RTF) o un URL di un sito Web che visualizza le note sulla versione.

- `<Icon>` - Questo elemento facoltativo è un percorso relativo di un file di immagine (png, bmp, jpeg, ico) contenuto nel pacchetto. L'immagine dell'icona deve essere di 32x32 pixel (o verrà ridotta a tale dimensione) e verrà visualizzata nell'interfaccia utente della visualizzazione elenco. Se non viene `Icon` specificato alcun elemento, l'interfaccia utente usa un valore predefinito.

- `<PreviewImage>` - Questo elemento facoltativo è un percorso relativo di un file di immagine (png, bmp, jpeg) contenuto nel pacchetto. L'immagine di anteprima deve essere di 200x200 pixel e visualizzata nell'interfaccia utente dei dettagli. Se non viene `PreviewImage` specificato alcun elemento, l'interfaccia utente usa un valore predefinito.

- `<Tags>` - Questo elemento facoltativo elenca i tag di testo aggiuntivi delimitati da punto e virgola usati per i suggerimenti per la ricerca. `Tags`L'elemento è limitato a 100 caratteri.

- `<GettingStartedGuide>` - Questo elemento facoltativo è un percorso relativo di un file HTML o un URL di un sito Web che contiene informazioni su come usare l'estensione o il contenuto all'interno di questo pacchetto. Questa guida viene avviata come parte di un'installazione.

- `<AnyElement>*` - Lo schema del manifesto è sufficientemente flessibile da consentire qualsiasi altro elemento. Tutti gli elementi figlio non riconosciuti dal caricatore del manifesto vengono esposti come elenco di oggetti XmlElement. Usando questi elementi figlio, le estensioni VSIX possono definire dati aggiuntivi nel file manifesto ed enumerarli in fase di esecuzione.

### <a name="installation-element"></a>Elemento Installation
 Questa sezione definisce la modalità di installazione del pacchetto e gli SKU dell'applicazione in cui può essere installato. Questa sezione contiene gli attributi seguenti:

- `Experimental` - Impostare questo attributo su true se si dispone di un'estensione attualmente installata per tutti gli utenti, ma si sta sviluppando una versione aggiornata nello stesso computer. Ad esempio, se MyExtension 1.0 è stato installato per tutti gli utenti, ma si vuole eseguire il debug di MyExtension 2.0 nello stesso computer, impostare Experimental="true". Questo attributo è disponibile in Visual Studio 2015 Update 1 e versioni successive.

- `Scope` - Questo attributo può assumere il valore "Global" o "ProductExtension":

  - "Global" specifica che l'ambito dell'installazione non è uno SKU specifico. Ad esempio, questo valore viene usato quando viene installato un SDK di estensione.

  - "ProductExtension" specifica che è installata un'estensione VSIX tradizionale (versione 1.0) con ambito Visual Studio SKU. Si tratta del valore predefinito.

- `AllUsers` - Questo attributo facoltativo specifica se il pacchetto verrà installato per tutti gli utenti. Per impostazione predefinita, questo attributo è false, che specifica che il pacchetto è per utente. Quando si imposta questo valore su true, l'utente che esegue l'installazione deve elevare al livello di privilegi amministrativi per installare il file VSIX risultante.

- `InstalledByMsi` : questo attributo facoltativo specifica se il pacchetto viene installato da un'applicazione msi. I pacchetti installati da un file MSI vengono installati e gestiti da MSI (Programmi e funzionalità) e non da Visual Studio Extension Manager.  Per impostazione predefinita, questo attributo è false, che specifica che il pacchetto non è installato da un file MSI.

- `SystemComponent` - Questo attributo facoltativo specifica se questo pacchetto deve essere considerato un componente di sistema. I componenti di sistema non vengono visualizzati nell'interfaccia utente di Gestione estensioni e non possono essere aggiornati. Per impostazione predefinita, questo attributo è false, che specifica che il pacchetto non è un componente di sistema.

- `AnyAttribute*` - L'elemento accetta un set aperto di attributi che verranno esposti in fase di esecuzione `Installation` come dizionario di coppie nome-valore.

- `<InstallationTarget>` -Questo elemento controlla il percorso in cui il programma di installazione VSIX installa il pacchetto. Se il valore dell'attributo è "ProductExtension", il pacchetto deve avere come destinazione uno SKU, che ha installato un file manifesto come parte del relativo contenuto per annunciarne la disponibilità `Scope` alle estensioni. `<InstallationTarget>`L'elemento ha gli attributi seguenti quando `Scope` l'attributo ha il valore esplicito o predefinito "ProductExtension":

  - `Id` - Questo attributo identifica il pacchetto.  L'attributo segue la convenzione dello spazio dei nomi: Company.Product.Feature.Name. `Id`L'attributo può contenere solo caratteri alfanumerici ed è limitato a 100 caratteri. Valori previsti:

    - Microsoft.VisualStudio.IntegratedShell

    - Microsoft.VisualStudio. Pro

    - Microsoft.VisualStudio. Premium

    - Microsoft.VisualStudio.Ultimate

    - Microsoft.VisualStudio.VWDExpress

    - Microsoft.VisualStudio.VPDExpress

    - Microsoft.VisualStudio.VSWinExpress

    - Microsoft.VisualStudio.VSLS

    - My.Shell.App

  - `Version` - Questo attributo specifica un intervallo di versioni con le versioni minime e massime supportate di questo SKU. Un pacchetto può visualizzare in dettaglio le versioni degli SKU supportati. La notazione dell'intervallo di versioni è [10.0 - 11.0], dove

    - [ - versione minima inclusiva.

    - ] - versione massima inclusiva.

    - ( - versione minima esclusiva.

    - ) - versione massima esclusiva.

    - Versione singola # : solo la versione specificata.

    > [!IMPORTANT]
    > La versione 2.0 dello schema VSIX è stata introdotta Visual Studio 2012. Per usare questo schema è necessario Visual Studio 2012 o versione successiva nel computer e usare il VSIXInstaller.exe che fa parte di tale prodotto. È possibile usare come destinazione le versioni precedenti di Visual Studio con un Visual Studio 2012 o versione successiva di VSIXInstaller, ma solo usando le versioni successive del programma di installazione.

    Visual Studio numeri di versione 2017 sono disponibili in Visual Studio numeri di [build e date di rilascio.](../install/visual-studio-build-numbers-and-release-dates.md)

    Quando si esprime la versione per Visual Studio 2017, la versione secondaria deve sempre **essere 0.** Ad esempio, Visual Studio 2017 versione 15.3.26730.0 deve essere espresso come [15.0.26730.0,16.0). Questa operazione è necessaria solo per i Visual Studio 2017 e versioni successive.

  - `AnyAttribute*` - L'elemento consente un set aperto di attributi esposti in fase di esecuzione `<InstallationTarget>` come dizionario di coppia nome-valore.

### <a name="dependencies-element"></a>Elemento Dependencies
 Questo elemento contiene un elenco di dipendenze dichiarate da questo pacchetto. Se vengono specificate dipendenze, tali pacchetti (identificati dalla relativa `Id` ) devono essere stati installati in precedenza.

- `<Dependency>` element : questo elemento figlio ha gli attributi seguenti:

  - `Id` - Questo attributo deve essere un ID univoco per il pacchetto dipendente. Questo valore Identity deve corrispondere `<Metadata><Identity>Id` all'attributo di un pacchetto da cui dipende questo pacchetto. `Id`L'attributo segue la convenzione dello spazio dei nomi: Company.Product.Feature.Name. L'attributo può contenere solo caratteri alfanumerici ed è limitato a 100 caratteri.

  - `Version` - Questo attributo specifica un intervallo di versioni con le versioni minime e massime supportate di questo SKU. Un pacchetto può visualizzare in dettaglio le versioni degli SKU supportati. La notazione dell'intervallo di versioni è [12.0, 13.0], dove:

    - [ - versione minima inclusiva.

    - ] - versione massima inclusiva.

    - ( - versione minima esclusiva.

    - ) - versione massima esclusiva.

    - Versione singola # : solo la versione specificata.

  - `DisplayName` - Questo attributo è il nome visualizzato del pacchetto dipendente, usato negli elementi dell'interfaccia utente, ad esempio finestre di dialogo e messaggi di errore. L'attributo è facoltativo, a meno che il pacchetto dipendente non sia installato dal servizio di installazione del servizio app.

  - `Location` - Questo attributo facoltativo specifica il percorso relativo all'interno di questo vsix a un pacchetto VSIX annidato o un URL al percorso di download per la dipendenza. Questo attributo viene usato per consentire all'utente di individuare il pacchetto dei prerequisiti.

  - `AnyAttribute*` - L'elemento accetta un set aperto di attributi che verranno esposti in fase di esecuzione come dizionario `Dependency` di coppia nome-valore.

### <a name="assets-element"></a>Elemento Assets
 Questo elemento contiene un elenco di tag per ogni estensione o elemento di contenuto `<Asset>` visualizzato da questo pacchetto.

- `<Asset>` - Questo elemento contiene gli attributi e gli elementi seguenti:

  - `Type` - Tipo di estensione o contenuto rappresentato da questo elemento. Ogni `<Asset>` elemento deve avere un singolo , ma più elementi possono avere lo stesso `Type` `<Asset>` `Type` . Questo attributo deve essere rappresentato come nome completo, in base alle convenzioni dello spazio dei nomi. I tipi noti sono:

    1. Microsoft.VisualStudio.VsPackage

    2. Microsoft.VisualStudio.MefComponent

    3. Microsoft.VisualStudio.ToolboxControl

    4. Microsoft.VisualStudio.Samples

    5. Microsoft.VisualStudio.ProjectTemplate

    6. Microsoft.VisualStudio.ItemTemplate

    7. Microsoft.VisualStudio.Assembly

       È possibile creare tipi personalizzati e assegnare loro nomi univoci. In fase di esecuzione all'interno Visual Studio, il codice può enumerare e accedere a questi tipi personalizzati tramite l'API di Gestione estensioni.

  - `Path` : percorso relativo del file o della cartella all'interno del pacchetto che contiene l'asset.

  - `TargetVersion` : intervallo di versioni a cui si applica l'asset specificato. Usato per la spedizione di più versioni di asset a versioni diverse di Visual Studio. Richiede Visual Studio 2017.3 o versione più recente per avere effetto.

  - `AnyAttribute*` : set aperto di attributi esposti in fase di esecuzione come dizionario di coppia nome-valore.

    `<AnyElement>*` - Qualsiasi contenuto strutturato è consentito tra un `<Asset>` tag di inizio e un tag di fine. Tutti gli elementi vengono esposti come elenco di oggetti XmlElement. Le estensioni VSIX possono definire metadati specifici del tipo strutturato nel file manifesto ed enumerarli in fase di esecuzione.

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

## <a name="see-also"></a>Vedi anche

- [Spedire Visual Studio estensioni](../extensibility/shipping-visual-studio-extensions.md)
