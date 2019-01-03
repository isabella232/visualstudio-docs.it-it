---
title: Riferimenti su VSIX Extension Schema 2.0 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6f9019ca281dd86ef4665e8f6590798d4dfbd917
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914666"
---
# <a name="vsix-extension-schema-20-reference"></a>Riferimenti su VSIX extension schema 2.0
Un file manifesto di distribuzione VSIX descrive il contenuto di un pacchetto VSIX. Il formato del file è disciplinato da uno schema. La versione 2.0 di questo schema supporta l'aggiunta di attributi e i tipi personalizzati.  Lo schema del manifesto è estendibile. Il caricatore di manifesto ignora gli elementi XML e gli attributi che non comprende.  
  
> [!IMPORTANT]
>  Visual Studio 2015 è possibile caricare i file VSIX nei formati Visual Studio 2010, Visual Studio 2012 o Visual Studio 2013.  
  
## <a name="package-manifest-schema"></a>Schema del manifesto del pacchetto  
 L'elemento radice del file manifesto XML è `<PackageManifest>`. Dispone di un singolo attributo `Version`, ovvero la versione del formato del manifesto. Se vengono apportate modifiche significative al formato, viene modificato il formato della versione. Questo articolo descrive una versione del formato manifesto 2.0, che viene specificato nel manifesto impostando il `Version` attributo il valore della versione = "2.0".  
  
### <a name="packagemanifest-element"></a>Elemento PackageManifest  
 All'interno di `<PackageManifest>` elemento radice, è possibile usare gli elementi seguenti:  
  
-   `<Metadata>` -Metadati e informazioni di annunci sul pacchetto stesso. Un solo `Metadata` è consentito nel manifesto dell'elemento.  
  
-   `<Installation>` -Questa sezione definisce il modo in cui in che è possibile installare questo pacchetto di estensione, inclusi gli SKU dell'applicazione che è possibile installare. Una sola `Installation` è consentito nel manifesto dell'elemento. Un manifesto deve avere un `Installation` elemento o questo pacchetto non verrà installato in qualsiasi SKU.  
  
-   `<Dependencies>` -Un elenco facoltativo delle dipendenze per questo pacchetto vengono definiti qui.  
  
-   `<Assets>` -Questa sezione contiene tutti gli asset contenuti all'interno di questo pacchetto. Senza questa sezione di questo pacchetto non verrà superficie qualsiasi contenuto.  
  
-   `<AnyElement>*` -Lo schema del manifesto è sufficientemente flessibile da consentire tutti gli altri elementi. Elementi figlio non riconosciuti dal caricatore del manifesto vengono esposte nell'API di Gestione estensioni come oggetti XmlElement aggiuntivi. Utilizza tali elementi figlio, le estensioni VSIX possono definire dati aggiuntivi nel file manifesto del codice in esecuzione in Visual Studio possa accedere in fase di esecuzione. Vedere <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements%2A> e <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.LocalizedAdditionalElements%2A>.  
  
### <a name="metadata-element"></a>Elemento dei metadati  
 In questa sezione è i metadati sul pacchetto, la propria identità e pubblicità informazioni. `<Metadata>` contiene gli elementi seguenti:  
  
-   `<Identity>` -Definisce le informazioni di identificazione del pacchetto e include gli attributi seguenti:  
  
    -   `Id` -Questo attributo deve essere un ID univoco per il pacchetto scelto dall'autore. Il nome deve essere qualificato esattamente i tipi CLR sono con spazio dei nomi: Company.Product.Feature.Name. Il `Id` attributo è limitato a 100 caratteri.  
  
    -   `Version` -Definisce la versione di questo pacchetto e il relativo contenuto. Questo attributo viene indicato il formato di controllo delle versioni di assembly CLR: Revisione (1.2.40308.00). Un pacchetto con un numero di versione superiore viene considerato aggiornamenti del pacchetto e può essere installato tramite le versioni esistenti.  
  
    -   `Language` -Questo attributo è la lingua predefinita per il pacchetto e corrisponde ai dati testuali di questo manifesto. Questo attributo segue la convenzione di codice delle impostazioni locali CLR per gli assembly di risorse, ad esempio: en-us, en, fr-fr. È possibile specificare `neutral` per dichiarare un'estensione indipendente dalla lingua che verrà eseguito in qualsiasi versione di Visual Studio. Il valore predefinito è `neutral`.  
  
    -   `Publisher` -Questo attributo identifica il server di pubblicazione del pacchetto, una società o per singole. Il `Publisher` attributo è limitato a 100 caratteri.  
  
-   `<DisplayName>` -Questo elemento specifica il nome del pacchetto semplice che viene visualizzato nella UI di Gestione estensioni. Il `DisplayName` contenuto è limitato a 50 caratteri.  
  
-   `<Description>` -Questo elemento facoltativo è una breve descrizione del pacchetto e il relativo contenuto che viene visualizzata in Gestione estensioni UI. Il `Description` contenuto può contenere qualsiasi testo che si desidera, ma ha limitato ai 1000 caratteri.  
  
-   `<MoreInfo>` -Questo elemento facoltativo è un URL di una pagina online che contiene una descrizione completa di questo pacchetto. Il protocollo deve essere specificato come http.  
  
-   `<License>` -Questo elemento facoltativo è un percorso relativo in un file di licenza (file con estensione txt,. RTF) contenuto nel pacchetto.  
  
-   `<ReleaseNotes>` -Questo elemento facoltativo è un percorso relativo in un file di note sulla versione contenuto nel pacchetto (con estensione txt,. RTF) oppure un URL a un sito Web che consente di visualizzare le note sulla versione.  
  
-   `<Icon>` -Questo elemento facoltativo è un percorso relativo a un file di immagine (png, bmp, jpeg, ico) contenuto nel pacchetto. L'immagine dell'icona devono essere 32 x 32 pixel (o verrà ridotta la dimensione desiderata) e viene visualizzato nel controllo listview dell'interfaccia utente. Se nessun `Icon` viene specificato alcun elemento, l'interfaccia utente usa un valore predefinito.  
  
-   `<PreviewImage>` -Questo elemento facoltativo è un percorso relativo a un file di immagine (png, bmp, jpeg) contenuto nel pacchetto. L'immagine di anteprima deve essere 200x200 pixel e visualizzate nei dettagli dell'interfaccia utente. Se nessun `PreviewImage` viene specificato alcun elemento, l'interfaccia utente usa un valore predefinito.  
  
-   `<Tags>` -Questo elemento facoltativo Elenca le categorie di testo delimitato da punto e virgola aggiuntivo che vengono utilizzati per i suggerimenti di ricerca. Il `Tags` elemento è limitato a 100 caratteri.  
  
-   `<GettingStartedGuide>` -Questo elemento facoltativo è un percorso relativo in un file HTML o un URL a un sito Web che contiene informazioni su come usare l'estensione o il contenuto all'interno di questo pacchetto. Questa guida viene avviata come parte di un'installazione.  
  
-   `<AnyElement>*` -Lo schema del manifesto è sufficientemente flessibile da consentire tutti gli altri elementi. Elementi figlio che non sono riconosciuti dal caricatore del manifesto vengono esposti come un elenco di oggetti XmlElement. Utilizza tali elementi figlio, le estensioni VSIX possono definire dati aggiuntivi nel file manifesto ed enumerarle in fase di esecuzione.  
  
### <a name="installation-element"></a>Elemento di installazione  
 Questa sezione definisce il modo in cui che questo pacchetto può essere installato e gli SKU dell'applicazione che è possibile installare in. In questa sezione contiene gli attributi seguenti:  
  
-   `Experimental` -Impostare questo attributo su true se si dispone di un'estensione che è attualmente installata per tutti gli utenti, ma si sta sviluppando una versione aggiornata nello stesso computer. Ad esempio, se sono stati installati MyExtension 1.0 per tutti gli utenti, ma si desidera eseguire il debug MyExtension 2.0 nello stesso computer, impostare sperimentale = "true". Questo attributo è disponibile in Visual Studio 2015 Update 1 e versioni successive.  
  
-   `Scope` -Questo attributo può accettare il valore "Globale" o "ProductExtension":  
  
    -   "Globale" Specifica che l'installazione non ha l'ambito per uno SKU specifico. Ad esempio, questo valore viene utilizzato quando viene installato un SDK di estensione.  
  
    -   "ProductExtension" Specifica che un'estensione VSIX tradizionale (versione 1.0) nell'ambito di singoli SKU di Visual Studio sia installata. Rappresenta il valore predefinito.  
  
-   `AllUsers` -Questo attributo facoltativo specifica se questo pacchetto verrà installato per tutti gli utenti. Per impostazione predefinita, questo attributo è false, che indica che il pacchetto per ogni utente. (Quando si imposta questo valore su true, l'utente di installazione deve elevare al livello di privilegi amministrativi per installare il progetto VSIX risultante.  
  
-   `InstalledByMsi` -Questo attributo facoltativo specifica se questo pacchetto viene installato da un file MSI. I pacchetti installati da un file MSI vengono installati e gestiti da identità del servizio gestito (programmi e funzionalità) e non per la gestione estensioni Visual Studio.  Per impostazione predefinita, questo attributo è false, che consente di specificare che il pacchetto non è installato da un file MSI.  
  
-   `SystemComponent` -Questo attributo facoltativo specifica se il pacchetto deve essere considerato un componente del sistema. I componenti di sistema non vengono visualizzate nella UI di Gestione estensioni e non possono essere aggiornati. Per impostazione predefinita, questo attributo è false, che consente di specificare che il pacchetto non è un componente del sistema.  
  
-   `AnyAttribute*` -La `Installation` elemento accetta un set aperto di attributi che verranno esposte in fase di esecuzione come un dizionario di coppie nome-valore.  
  
-   `<InstallationTarget>` : Questo elemento controlla il percorso in cui il programma di installazione VSIX installa il pacchetto. Se il valore della `Scope` attributo è "ProductExtension" il pacchetto deve avere come destinazione uno SKU, che ha installato un file manifesto come parte del relativo contenuto per annunciare la disponibilità per le estensioni. Il `<InstallationTarget>` elemento prevede i seguenti attributi quando la `Scope` attributo è l'impostazione esplicita o il valore predefinito "ProductExtension":  
  
    -   `Id` -Questo attributo identifica il pacchetto.  L'attributo segue la convenzione di spazio dei nomi: Company.Product.Feature.Name. Il `Id` attributo può contenere solo caratteri alfanumerici ed è limitato a 100 caratteri. Valori previsti:  
  
        -   Microsoft.VisualStudio.IntegratedShell  
  
        -   Microsoft.VisualStudio.Pro  
  
        -   Microsoft.VisualStudio.Premium  
  
        -   Microsoft.VisualStudio.Ultimate  
  
        -   Microsoft.VisualStudio.VWDExpress  
  
        -   Microsoft.VisualStudio.VPDExpress  
  
        -   Microsoft.VisualStudio.VSWinExpress  
  
        -   Microsoft.VisualStudio.VSLS  
  
        -   My.Shell.App  
  
    -   `Version` -Questo attributo specifica un intervallo di versioni con le versioni supportate di minime e massime di questo SKU. Un pacchetto può descrivere in dettaglio le versioni degli SKU che supporta. La notazione di intervallo di versione è [11.0 10.0], dove  
  
        -   [-versione minima inclusiva.  
  
        -   ]-versione massima inclusivo.  
  
        -   (-versione minima esclusiva.  
  
        -   )-versione massima esclusivo.  
  
        -   Versione unica & - solo la versione specificata.  
  
        > [!IMPORTANT]
        >  Versione 2.0 dello Schema VSIX è stata introdotta in Visual Studio 2012. Usare questo schema è necessario che Visual Studio 2012 o in un secondo momento è installato nel computer e usare VSIXInstaller.exe che fa parte di tale prodotto. È possibile destinate alle versioni precedenti di Visual Studio con un Visual Studio 2012 o versioni successive VSIX Installer, ma solo usando le versioni più recenti del programma di installazione. 
        
        I numeri di versione di Visual Studio 2017 reperibili [numeri di build e date di rilascio di Visual Studio](../install/visual-studio-build-numbers-and-release-dates.md).
        
        Quando si esprime la versione per le versioni di Visual Studio 2017, deve essere sempre la versione secondaria **0**. Ad esempio, Visual Studio 2017 versione 15.3.26730.0 deve essere espresso come [15.0.26730.0,16.0). Questo è solo necessario per i numeri di versione di Visual Studio 2017.
  
    -   `AnyAttribute*` -La `<InstallationTarget>` elemento consente un set aperto di attributi esposti in fase di esecuzione come un dizionario di coppie nome-valore.  
  
### <a name="dependencies-element"></a>Elemento di dipendenze  
 Questo elemento contiene un elenco di dipendenze che dichiara questo pacchetto. Se vengono specificate le eventuali dipendenze, tali pacchetti (identificato dal loro `Id`) sia stato installato prima.  
  
-   `<Dependency>` elemento - l'elemento figlio ha gli attributi seguenti:  
  
    -   `Id` -Questo attributo deve essere un ID univoco per il pacchetto dipendente. Questo valore di identità deve corrispondere il `<Metadata><Identity>Id` attributo di un pacchetto di cui dipende questo pacchetto. Il `Id` attributo segue la convenzione di spazio dei nomi: Company.Product.Feature.Name. L'attributo può contenere solo caratteri alfanumerici ed è limitato a 100 caratteri.  
  
    -   `Version` -Questo attributo specifica un intervallo di versioni con le versioni supportate di minime e massime di questo SKU. Un pacchetto può descrivere in dettaglio le versioni degli SKU che supporta. La notazione di intervallo di versione è [12.0, 13.0], dove:  
  
        -   [-versione minima inclusiva.  
  
        -   ]-versione massima inclusivo.  
  
        -   (-versione minima esclusiva.  
  
        -   )-versione massima esclusivo.  
  
        -   Versione unica & - solo la versione specificata.  
  
    -   `DisplayName` -Questo attributo è il nome visualizzato del pacchetto dipendente, che viene usato negli elementi dell'interfaccia utente, ad esempio le finestre di dialogo e messaggi di errore. L'attributo è facoltativo, a meno che non è installato il pacchetto dipendente dall'identità del servizio gestito.  
  
    -   `Location` -Questo attributo facoltativo specifica il percorso relativo all'interno di questa estensione VSIX a un pacchetto VSIX annidato o un URL al percorso di download per la dipendenza. Questo attributo viene usato per consentire all'utente di individuare il pacchetto dei prerequisiti.  
  
    -   `AnyAttribute*` -La `Dependency` elemento accetta un set aperto di attributi che verranno esposte in fase di esecuzione come un dizionario di coppie nome-valore.  
  
### <a name="assets-element"></a>Elemento Asset  
 Questo elemento contiene un elenco di `<Asset>` tag per ogni elemento di estensione o il contenuto esposto da questo pacchetto.  
  
- `<Asset>` -Questo elemento contiene elementi e gli attributi seguenti:  
  
  - `Type` -Tipo di estensione o contenuto rappresentato da questo elemento. Ciascuna `<Asset>` elemento deve avere un unico `Type`, ma più `<Asset>` elementi possono avere lo stesso `Type`. Questo attributo deve essere rappresentato come un nome completo, in base alle convenzioni dello spazio dei nomi. I tipi noti sono:  
  
    1. Microsoft.VisualStudio.VsPackage  
  
    2. Microsoft.VisualStudio.MefComponent  
  
    3. Microsoft.VisualStudio.ToolboxControl  
  
    4. Microsoft.VisualStudio.Samples  
  
    5. Microsoft.VisualStudio.ProjectTemplate  
  
    6. Microsoft.VisualStudio.ItemTemplate  
  
    7. Microsoft.VisualStudio.Assembly  
  
       È possibile creare tipi personalizzati e assegnare loro nomi univoci. In fase di esecuzione all'interno di Visual Studio, il codice può enumerare e accedere a questi tipi personalizzati tramite l'API di Gestione estensioni.  
  
  - `Path` -il percorso relativo del file o cartella all'interno del pacchetto che contiene l'asset.  
    
  - `TargetVersion` -l'intervallo di versioni a cui si applica l'asset specificato. Usare per la spedizione di più versioni degli asset a versioni diverse di Visual Studio. Richiede Visual Studio ha effetto 2017.3 o versione successiva.
  
  - `AnyAttribute*` -Un set aperto di attributi esposti in fase di esecuzione come un dizionario di coppia nome-valore.  
  
     `<AnyElement>*` -Qualsiasi contenuto strutturato è consentita tra un `<Asset>` begin ed end tag. Tutti gli elementi sono esposti come un elenco di oggetti XmlElement. Le estensioni VSIX è possono definire i metadati specifici del tipo strutturato nel file manifesto ed enumerarle in fase di esecuzione.  
  
### <a name="sample-manifest"></a>Manifesto di esempio  
  
```  
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
 [Estensioni di Visual Studio di spedizione](../extensibility/shipping-visual-studio-extensions.md)
