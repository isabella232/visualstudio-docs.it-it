---
title: Guida di riferimento allo schema di estensione VSIX 2,0 | Microsoft Docs
description: Lo schema di estensione VSIX 2,0 definisce il formato di file per un file manifesto di distribuzione VSIX, che descrive il contenuto di un pacchetto VSIX.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3fdbd9220ef82102dd66f10ab7f15570118bae9a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904539"
---
# <a name="vsix-extension-schema-20-reference"></a>Riferimento allo schema di estensione VSIX 2,0
Un file manifesto di distribuzione VSIX descrive il contenuto di un pacchetto VSIX. Il formato del file è regolato da uno schema. La versione 2,0 di questo schema supporta l'aggiunta di tipi e attributi personalizzati.  Lo schema del manifesto è estendibile. Il caricatore del manifesto ignora gli elementi e gli attributi XML che non sono in grado di comprendere.

> [!IMPORTANT]
> Visual Studio 2015 è in grado di caricare file VSIX nei formati Visual Studio 2010, Visual Studio 2012 o Visual Studio 2013.

## <a name="package-manifest-schema"></a>Schema del manifesto del pacchetto
 L'elemento radice del file XML del manifesto è `<PackageManifest>` . Ha un solo attributo `Version` , ovvero la versione del formato del manifesto. Se vengono apportate modifiche importanti al formato, il formato della versione viene modificato. Questo articolo descrive la versione del formato manifesto 2,0, specificata nel manifesto impostando l' `Version` attributo sul valore Version = "2.0".

### <a name="packagemanifest-element"></a>Elemento PackageManifest
 All'interno dell' `<PackageManifest>` elemento radice è possibile utilizzare gli elementi seguenti:

- `<Metadata>` -Metadati e informazioni pubblicitarie sul pacchetto stesso. `Metadata`Nel manifesto è consentito un solo elemento.

- `<Installation>` -In questa sezione viene definito il modo in cui è possibile installare questo pacchetto di estensione, inclusi gli SKU dell'applicazione in cui è possibile eseguire l'installazione. `Installation`Nel manifesto è consentito un solo elemento. Un manifesto deve avere un `Installation` elemento o questo pacchetto non verrà installato in alcuno SKU.

- `<Dependencies>` -Un elenco facoltativo di dipendenze per questo pacchetto è definito qui.

- `<Assets>` -In questa sezione sono contenuti tutti gli asset contenuti nel pacchetto. Senza questa sezione, il pacchetto non rilascerà alcun contenuto.

- `<AnyElement>*` -Lo schema del manifesto è sufficientemente flessibile per consentire qualsiasi altro elemento. Tutti gli elementi figlio non riconosciuti dal caricatore del manifesto vengono esposti nell'API di gestione estensioni come oggetti XmlElement aggiuntivi. Usando questi elementi figlio, le estensioni VSIX possono definire dati aggiuntivi nel file manifesto che possono accedere al codice in esecuzione in Visual Studio in fase di esecuzione. Vedere [Microsoft. VisualStudio. ExtensionManager. IExtension. AdditionalElements](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120)).

### <a name="metadata-element"></a>Elemento Metadata
 In questa sezione vengono illustrati i metadati relativi al pacchetto, alla relativa identità e alle informazioni pubblicitarie. `<Metadata>` contiene gli elementi seguenti:

- `<Identity>` -Definisce le informazioni di identificazione per il pacchetto e include i seguenti attributi:

  - `Id` : Questo attributo deve essere un ID univoco per il pacchetto scelto dall'autore. Il nome deve essere qualificato nello stesso modo in cui i tipi CLR sono spazi dei nomi: Company.Product.Feature.Name. L' `Id` attributo è limitato a 100 caratteri.

  - `Version` : Definisce la versione del pacchetto e il relativo contenuto. Questo attributo segue il formato del controllo delle versioni dell'assembly CLR: Major. minor. Build. Revision (1.2.40308.00). Un pacchetto con un numero di versione superiore viene considerato aggiornamenti del pacchetto e può essere installato tramite la versione installata esistente.

  - `Language` -Questo attributo è la lingua predefinita per il pacchetto e corrisponde ai dati testuali in questo manifesto. Questo attributo segue la convenzione di codice delle impostazioni locali CLR per gli assembly di risorse, ad esempio: en-US, en, fr-fr. È possibile specificare `neutral` di dichiarare un'estensione indipendente dalla lingua che potrà essere eseguita in qualsiasi versione di Visual Studio. Il valore predefinito è `neutral`.

  - `Publisher` : Questo attributo identifica l'autore del pacchetto, ovvero un nome aziendale o un nome singolo. L' `Publisher` attributo è limitato a 100 caratteri.

- `<DisplayName>` -Questo elemento specifica il nome del pacchetto descrittivo visualizzato nell'interfaccia utente di gestione estensioni. Il `DisplayName` contenuto è limitato a 50 caratteri.

- `<Description>` -Questo elemento facoltativo è una breve descrizione del pacchetto e del relativo contenuto visualizzato nell'interfaccia utente di gestione estensioni. Il `Description` contenuto può contenere qualsiasi testo desiderato, ma è limitato a 1000 caratteri.

- `<MoreInfo>` -Questo elemento facoltativo è un URL di una pagina online che contiene una descrizione completa del pacchetto. Il protocollo deve essere specificato come http.

- `<License>` -Questo elemento facoltativo è un percorso relativo di un file di licenza (con estensione txt, RTF) contenuto nel pacchetto.

- `<ReleaseNotes>` -Questo elemento facoltativo è un percorso relativo di un file delle note sulla versione contenuto nel pacchetto (con estensione txt, RTF) oppure un URL di un sito Web in cui vengono visualizzate le note sulla versione.

- `<Icon>` -Questo elemento facoltativo è un percorso relativo di un file di immagine (PNG, BMP, JPEG, ICO) contenuto nel pacchetto. L'immagine dell'icona deve essere 32x32 pixel (o verrà ridotta a tale dimensione) e verrà visualizzata nell'interfaccia utente di ListView. Se non `Icon` viene specificato alcun elemento, l'interfaccia utente utilizzerà un valore predefinito.

- `<PreviewImage>` -Questo elemento facoltativo è un percorso relativo di un file di immagine (PNG, BMP, jpeg) contenuto nel pacchetto. L'immagine di anteprima deve essere 200x200 pixel e visualizzata nell'interfaccia utente di dettagli. Se non `PreviewImage` viene specificato alcun elemento, l'interfaccia utente utilizzerà un valore predefinito.

- `<Tags>` -Questo elemento facoltativo elenca i tag di testo delimitati da punti e virgola aggiuntivi usati per gli hint di ricerca. L' `Tags` elemento è limitato a 100 caratteri.

- `<GettingStartedGuide>` -Questo elemento facoltativo è un percorso relativo di un file HTML o un URL di un sito Web che contiene informazioni su come usare l'estensione o il contenuto all'interno di questo pacchetto. Questa guida viene avviata come parte di un'installazione di.

- `<AnyElement>*` -Lo schema del manifesto è sufficientemente flessibile per consentire qualsiasi altro elemento. Tutti gli elementi figlio che non sono riconosciuti dal caricatore del manifesto vengono esposti come un elenco di oggetti XmlElement. Usando questi elementi figlio, le estensioni VSIX possono definire dati aggiuntivi nel file manifesto ed enumerarli in fase di esecuzione.

### <a name="installation-element"></a>Elemento di installazione
 Questa sezione definisce la modalità di installazione del pacchetto e gli SKU dell'applicazione in cui è possibile eseguire l'installazione. Questa sezione contiene gli attributi seguenti:

- `Experimental` -Impostare questo attributo su true se si dispone di un'estensione attualmente installata per tutti gli utenti, ma si sta sviluppando una versione aggiornata nello stesso computer. Se, ad esempio, è stata installata l'estensione 1,0 per tutti gli utenti, ma si desidera eseguire il debug di estensione 2,0 nello stesso computer, impostare experimental = "true". Questo attributo è disponibile in Visual Studio 2015 Update 1 e versioni successive.

- `Scope` -Questo attributo può assumere il valore "Global" o "ProductExtension":

  - "Globale" specifica che l'ambito dell'installazione non è limitato a uno SKU specifico. Questo valore, ad esempio, viene usato quando viene installato un SDK di estensione.

  - "ProductExtension" specifica che è installata un'estensione VSIX tradizionale (versione 1,0) con ambito per i singoli SKU di Visual Studio. Si tratta del valore predefinito.

- `AllUsers` -Questo attributo facoltativo specifica se il pacchetto verrà installato per tutti gli utenti. Per impostazione predefinita, questo attributo è false, che specifica che il pacchetto è per utente. Quando si imposta questo valore su true, l'utente che esegue l'installazione deve elevare il livello di privilegio amministrativo per installare il progetto VSIX risultante.

- `InstalledByMsi` -Questo attributo facoltativo specifica se il pacchetto viene installato da un file MSI. I pacchetti installati da un file MSI vengono installati e gestiti da MSI (programmi e funzionalità) e non da Gestione estensioni di Visual Studio.  Per impostazione predefinita, questo attributo è false, che specifica che il pacchetto non è installato da un file MSI.

- `SystemComponent` -Questo attributo facoltativo specifica se il pacchetto deve essere considerato un componente di sistema. I componenti di sistema non vengono visualizzati nell'interfaccia utente di gestione estensioni e non possono essere aggiornati. Per impostazione predefinita, questo attributo è false, che specifica che il pacchetto non è un componente di sistema.

- `AnyAttribute*` -L' `Installation` elemento accetta un set di attributi aperto che verrà esposto in fase di esecuzione come dizionario delle coppie nome/valore.

- `<InstallationTarget>` : Questo elemento controlla il percorso in cui il programma di installazione VSIX installa il pacchetto. Se il valore dell' `Scope` attributo è "ProductExtension", il pacchetto deve avere come destinazione uno SKU, che ha installato un file manifesto come parte del contenuto per annunciare la disponibilità alle estensioni. L' `<InstallationTarget>` elemento presenta gli attributi seguenti quando l' `Scope` attributo ha il valore esplicito o predefinito "ProductExtension":

  - `Id` : Questo attributo identifica il pacchetto.  L'attributo segue la convenzione dello spazio dei nomi: Company.Product.Feature.Name. L' `Id` attributo può contenere solo caratteri alfanumerici ed è limitato a 100 caratteri. Valori previsti:

    - Microsoft. VisualStudio. IntegratedShell

    - Microsoft.VisualStudio.Pro

    - Microsoft. VisualStudio. Premium

    - Microsoft. VisualStudio. Ultimate

    - Microsoft. VisualStudio. VWDExpress

    - Microsoft. VisualStudio. VPDExpress

    - Microsoft. VisualStudio. VSWinExpress

    - Microsoft. VisualStudio. VSLS

    - My. Shell. app

  - `Version` -Questo attributo specifica un intervallo di versioni con le versioni minime e massime supportate di questo SKU. Un pacchetto può illustrare in dettaglio le versioni degli SKU supportati. La notazione dell'intervallo di versioni è [10,0-11,0], dove

    - [-versione minima inclusiva.

    - ]-versione massima inclusa.

    - (-versione minima esclusiva.

    - )-versione massima esclusiva.

    - Versione singola: solo la versione specificata.

    > [!IMPORTANT]
    > La versione 2,0 dello schema VSIX è stata introdotta in Visual Studio 2012. Per utilizzare questo schema è necessario che nel computer sia installato Visual Studio 2012 o versione successiva e utilizzare il VSIXInstaller.exe che fa parte del prodotto. È possibile fare riferimento a versioni precedenti di Visual Studio con Visual Studio 2012 o versioni successive VSIX Installer, ma solo usando le versioni più recenti del programma di installazione.

    I numeri di versione di Visual Studio 2017 sono disponibili in [numeri di build di Visual Studio e date di rilascio](../install/visual-studio-build-numbers-and-release-dates.md).

    Quando si esprime la versione per le versioni di Visual Studio 2017, la versione secondaria deve sempre essere **0**. Ad esempio, Visual Studio 2017 versione 15.3.26730.0 dovrebbe essere espresso come [15.0.26730.0, 16). Questa operazione è necessaria solo per i numeri di versione di Visual Studio 2017 e versioni successive.

  - `AnyAttribute*` -L' `<InstallationTarget>` elemento consente un set aperto di attributi esposto in fase di esecuzione come dizionario delle coppie nome/valore.

### <a name="dependencies-element"></a>Elemento dipendenze
 Questo elemento contiene un elenco di dipendenze dichiarate da questo pacchetto. Se vengono specificate dipendenze, è necessario che i pacchetti (identificati da `Id` ) siano stati installati in precedenza.

- `<Dependency>` element: questo elemento figlio ha gli attributi seguenti:

  - `Id` : Questo attributo deve essere un ID univoco per il pacchetto dipendente. Questo valore Identity deve corrispondere all' `<Metadata><Identity>Id` attributo di un pacchetto da cui dipende questo pacchetto. L' `Id` attributo segue la convenzione dello spazio dei nomi: Company.Product.feature.Name. L'attributo può contenere solo caratteri alfanumerici ed è limitato a 100 caratteri.

  - `Version` -Questo attributo specifica un intervallo di versioni con le versioni minime e massime supportate di questo SKU. Un pacchetto può illustrare in dettaglio le versioni degli SKU supportati. La notazione dell'intervallo di versioni è [12,0, 13,0], dove:

    - [-versione minima inclusiva.

    - ]-versione massima inclusa.

    - (-versione minima esclusiva.

    - )-versione massima esclusiva.

    - Versione singola: solo la versione specificata.

  - `DisplayName` : Questo attributo è il nome visualizzato del pacchetto dipendente, utilizzato negli elementi dell'interfaccia utente, ad esempio le finestre di dialogo e i messaggi di errore. L'attributo è facoltativo, a meno che il pacchetto dipendente non venga installato da MSI.

  - `Location` -Questo attributo facoltativo specifica il percorso relativo all'interno di questo progetto VSIX per un pacchetto VSIX annidato o un URL per il percorso di download per la dipendenza. Questo attributo viene utilizzato per aiutare l'utente a individuare il pacchetto dei prerequisiti.

  - `AnyAttribute*` -L' `Dependency` elemento accetta un set di attributi aperto che verrà esposto in fase di esecuzione come dizionario delle coppie nome/valore.

### <a name="assets-element"></a>Elemento Assets
 Questo elemento contiene un elenco di `<Asset>` tag per ogni estensione o elemento di contenuto esposto da questo pacchetto.

- `<Asset>` -Questo elemento contiene gli attributi e gli elementi seguenti:

  - `Type` : Tipo di estensione o contenuto rappresentato da questo elemento. Ogni `<Asset>` elemento deve avere un singolo `Type` , ma più `<Asset>` elementi possono avere lo stesso valore `Type` . Questo attributo deve essere rappresentato come nome completo, in base alle convenzioni dello spazio dei nomi. I tipi noti sono:

    1. Microsoft. VisualStudio. VsPackage

    2. Microsoft.VisualStudio.MefComponent

    3. Microsoft. VisualStudio. ToolboxControl

    4. Microsoft. VisualStudio. Samples

    5. Microsoft. VisualStudio. ProjectTemplate

    6. Microsoft. VisualStudio. ItemTemplate

    7. Microsoft. VisualStudio. assembly

       È possibile creare tipi personalizzati e assegnare loro nomi univoci. In fase di esecuzione all'interno di Visual Studio, il codice può enumerare e accedere a questi tipi personalizzati tramite l'API di gestione estensioni.

  - `Path` : percorso relativo del file o della cartella all'interno del pacchetto che contiene l'asset.

  - `TargetVersion` : intervallo di versioni a cui si applica l'asset specificato. Usato per la distribuzione di più versioni di asset a versioni diverse di Visual Studio. Per avere effetto, è necessario Visual Studio 2017,3 o versione successiva.

  - `AnyAttribute*` : Set di attributi aperto esposto in fase di esecuzione come dizionario delle coppie nome/valore.

    `<AnyElement>*` -Qualsiasi contenuto strutturato è consentito tra un `<Asset>` tag di inizio e di fine. Tutti gli elementi vengono esposti come un elenco di oggetti XmlElement. Le estensioni VSIX possono definire metadati specifici dei tipi strutturati nel file manifesto ed enumerarli in fase di esecuzione.

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

- [Distribuire le estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
