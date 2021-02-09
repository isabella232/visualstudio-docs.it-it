---
title: Parametri sostituibili | Microsoft Docs
description: Esaminare i parametri sostituibili (token), che specificano i valori all'interno dei file di progetto per gli elementi della soluzione SharePoint i cui valori effettivi non sono noti in fase di progettazione.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload: office
ms.openlocfilehash: 3eb6e737a1f939e05e6a6be7f2c9ba950fc411d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889499"
---
# <a name="replaceable-parameters"></a>Parametri sostituibili
  I parametri sostituibili, o *token*, possono essere usati all'interno di file di progetto per fornire valori per gli elementi della soluzione SharePoint i cui valori effettivi non sono noti in fase di progettazione. Si tratta di funzioni simili ai token di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modello standard. Per ulteriori informazioni, vedere [parametri di modello](../ide/template-parameters.md).

## <a name="token-format"></a>Formato token
 I token iniziano e terminano con un segno di dollaro ($). Durante la distribuzione, tutti i token utilizzati vengono sostituiti con i valori effettivi quando un progetto viene inserito in un pacchetto di soluzione SharePoint (file con estensione *WSP* ). Il token **$SharePoint. Package.Name $** , ad esempio, potrebbe risolversi nella stringa "test SharePoint Package".

## <a name="token-rules"></a>Regole token
 Ai token si applicano le regole seguenti:

- I token possono essere specificati in qualsiasi punto di una riga.

- I token non possono estendersi su più righe.

- Lo stesso token può essere specificato più di una volta nella stessa riga e nello stesso file.

- È possibile specificare token diversi nella stessa riga.

  I token che non seguono queste regole vengono ignorati e non generano un avviso o un errore.

  La sostituzione dei token in base ai valori stringa viene eseguita immediatamente dopo la trasformazione del manifesto. Questa sostituzione consente all'utente di modificare i modelli di manifesto con i token.

### <a name="token-name-resolution"></a>Risoluzione dei nomi di token
 Nella maggior parte dei casi, un token viene risolto in un valore specifico indipendentemente dalla posizione in cui è contenuto. Tuttavia, se il token è correlato a un pacchetto o a una funzionalità, il valore del token dipende dalla posizione in cui è contenuto. Se, ad esempio, una funzionalità è nel pacchetto A, il token viene `$SharePoint.Package.Name$` risolto nel valore "pacchetto a". Se la stessa funzionalità è presente nel pacchetto B, viene `$SharePoint.Package.Name$` risolta in "pacchetto b".

## <a name="tokens-list"></a>Elenco dei token
 Nella tabella seguente sono elencati i token disponibili.

|Nome|Descrizione|
|----------|-----------------|
|$SharePoint. Project. FileName $|Nome del file di progetto che lo contiene, ad esempio *NewProj. csproj*.|
|$SharePoint. Project. Nomefilesenzaestensione $|Nome del file di progetto che lo contiene senza l'estensione del nome di file. Ad esempio, "NewProj".|
|$SharePoint. Project. AssemblyFullName $|Nome visualizzato (nome sicuro) dell'assembly di output del progetto che lo contiene.|
|$SharePoint. Project. AssemblyFileName $|Nome dell'assembly di output del progetto che lo contiene.|
|$SharePoint. Project. AssemblyFileNameWithoutExtension $|Nome dell'assembly di output del progetto contenitore, senza l'estensione del nome di file.|
|$SharePoint. Project. AssemblyPublicKeyToken $|Token di chiave pubblica dell'assembly di output del progetto che lo contiene, convertito in una stringa. (16 caratteri nel formato esadecimale "X2").|
|$SharePoint. Package.Name $|Nome del pacchetto che lo contiene.|
|$SharePoint. Package. FileName $|Nome del file di definizione del pacchetto che lo contiene.|
|$SharePoint. Package. Nomefilesenzaestensione $|Nome (senza estensione) del file di definizione del pacchetto che lo contiene.|
|$SharePoint. Package.Id $|ID di SharePoint per il pacchetto che lo contiene. Se una funzionalità viene usata in più di un pacchetto, questo valore verrà modificato.|
|$SharePoint. feature. FileName $|Nome del file di definizione della funzionalità che lo contiene, ad esempio *Feature1. feature*.|
|$SharePoint. feature. Nomefilesenzaestensione $|Nome del file di definizione della funzionalità senza l'estensione del nome di file.|
|$SharePoint. feature. DeploymentPath $|Nome della cartella che contiene la funzionalità nel pacchetto. Questo token equivale alla proprietà "percorso di distribuzione" nella finestra di progettazione della funzionalità. Un valore di esempio è "Project1_Feature1".|
|$SharePoint. Feature.Id $|ID di SharePoint della funzionalità che lo contiene. Questo token, come per tutti i token a livello di funzionalità, può essere utilizzato solo da file inclusi in un pacchetto tramite una funzionalità, non aggiunti direttamente a un pacchetto all'esterno di una funzionalità.|
|$SharePoint. ProjectItem.Name $|Il nome dell'elemento del progetto (non il nome file), come ottenuto da **ISharePointProjectItem.Name**.|
|$SharePoint. Type. \<GUID> . AssemblyQualifiedName $|Nome completo di assembly del tipo che corrisponde al [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] del token. Il formato del [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] è minuscolo e corrisponde al formato Guid.ToString("D"), vale a dire xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx.|
|$SharePoint. Type. \<GUID> . FullName $|Nome completo del tipo corrispondente al GUID nel token. Il formato del GUID è minuscolo e corrisponde al formato GUID. ToString ("D"), vale a dire xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx.|

## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>Aggiungere estensioni all'elenco di estensioni di file di sostituzione dei token
 Sebbene i token possano essere teoricamente utilizzati da qualsiasi file appartenente a un elemento del progetto SharePoint incluso nel pacchetto, per impostazione predefinita [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Cerca i token solo nei file del pacchetto, nei file manifesto e nei file con le seguenti estensioni:

- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]

- ASCX

- ASPX

- WebPart

- DWP

  Queste estensioni sono definite dall' `<TokenReplacementFileExtensions>` elemento nel file Microsoft. VisualStudio. SharePoint. targets, che si trova nella cartella... \\<Program Files \> \MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools.

  È tuttavia possibile aggiungere estensioni di file aggiuntive all'elenco. Aggiungere un `<TokenReplacementFileExtensions>` elemento a qualsiasi PropertyGroup nel file di progetto SharePoint definito prima del \<Import> del file delle destinazioni di SharePoint.

> [!NOTE]
> Poiché la sostituzione dei token si verifica dopo la compilazione di un progetto, non è necessario aggiungere estensioni di file per i tipi di file compilati, ad esempio *. cs*, *. vb* o *. resx*. I token vengono sostituiti solo nei file non compilati.

 Ad esempio, per aggiungere le estensioni di file (estensione estensione e *yourextension*) all'elenco di estensioni di file di sostituzione dei token, è necessario aggiungere il codice seguente a un file di progetto (con *estensione* *csproj*):

```xml
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
.
.
.
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>
</PropertyGroup>
```

 È possibile aggiungere l'estensione direttamente al file targets (*. targets*). Tuttavia, l'aggiunta dell'estensione modifica l'elenco di estensioni per tutti i progetti SharePoint inclusi nel sistema locale, non solo per quelli personalizzati. Questa estensione può essere utile quando si è l'unico sviluppatore del sistema o se la maggior parte dei progetti li richiede. Tuttavia, poiché è specifico del sistema, questo approccio non è portabile ed è quindi consigliabile aggiungere le estensioni al file di progetto.

## <a name="see-also"></a>Vedi anche
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
