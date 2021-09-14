---
title: Parametri sostituibili | Microsoft Docs
description: Esaminare i parametri sostituibili (token), che specificano i valori all'interno dei file di progetto SharePoint elementi della soluzione i cui valori effettivi non sono noti in fase di progettazione.
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
ms.technology: sharepoint-development
ms.workload: office
ms.openlocfilehash: e36edf6d8482fcb48a6a77695a6631aed1868203
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635579"
---
# <a name="replaceable-parameters"></a>Parametri sostituibili
  I parametri sostituibili, o *token,* possono essere usati all'interno dei file di progetto per fornire valori per SharePoint elementi della soluzione i cui valori effettivi non sono noti in fase di progettazione. Sono simili in funzione ai [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] token di modello standard. Per altre informazioni, vedere [Parametri del modello.](../ide/template-parameters.md)

## <a name="token-format"></a>Formato del token
 I token iniziano e terminano con un simbolo di dollaro ($). In fase di distribuzione, tutti i token usati vengono sostituiti con i valori effettivi quando un progetto viene in pacchetto SharePoint pacchetto della soluzione (file *con estensione wsp).* Ad esempio, il token **$SharePoint. Package.Name$** potrebbe risolversi nella stringa "Test SharePoint Package".

## <a name="token-rules"></a>Regole dei token
 Ai token si applicano le regole seguenti:

- I token possono essere specificati in qualsiasi punto di una riga.

- I token non possono estendersi su più righe.

- Lo stesso token può essere specificato più volte nella stessa riga e nello stesso file.

- È possibile che nella stessa riga siano specificati token diversi.

  I token che non seguono queste regole vengono ignorati e non comportano un avviso o un errore.

  La sostituzione dei token con i valori stringa viene eseguita immediatamente dopo la trasformazione del manifesto. Questa sostituzione consente all'utente di modificare i modelli di manifesto con i token.

### <a name="token-name-resolution"></a>Risoluzione dei nomi dei token
 Nella maggior parte dei casi, un token viene risolto in un valore specifico indipendentemente dalla posizione in cui è contenuto. Tuttavia, se il token è correlato a un pacchetto o a una funzionalità, il valore del token dipende dalla posizione in cui è contenuto. Ad esempio, se una funzionalità si trova nel pacchetto A, il token `$SharePoint.Package.Name$` viene risolto nel valore "Pacchetto A". Se la stessa funzionalità è presente nel pacchetto B, `$SharePoint.Package.Name$` viene risolto in "Pacchetto B".

## <a name="tokens-list"></a>Elenco di token
 Nella tabella seguente sono elencati i token disponibili.

|Nome|Descrizione|
|----------|-----------------|
|$SharePoint. Project. FileName$|Nome del file di progetto contenitore, ad esempio *NewProj.csproj.*|
|$SharePoint. Project. FileNameWithoutExtension$|Nome del file di progetto contenitore senza l'estensione del nome file. Ad esempio, "NewProj".|
|$SharePoint. Project. AssemblyFullName$|Nome visualizzato (nome sicuro) dell'assembly di output del progetto contenitore.|
|$SharePoint. Project. AssemblyFileName$|Nome dell'assembly di output del progetto contenitore.|
|$SharePoint. Project. AssemblyFileNameWithoutExtension$|Nome dell'assembly di output del progetto contenitore, senza l'estensione di file.|
|$SharePoint. Project. AssemblyPublicKeyToken$|Token di chiave pubblica dell'assembly di output del progetto contenitore, convertito in una stringa. (16 caratteri in formato esadecimale "x2".|
|$SharePoint. Package.Name$|Nome del pacchetto contenitore.|
|$SharePoint. Package.FileName$|Nome del file di definizione del pacchetto contenitore.|
|$SharePoint. Package.FileNameWithoutExtension$|Nome (senza estensione) del file di definizione del pacchetto contenitore.|
|$SharePoint. Package.Id$|ID SharePoint per il pacchetto contenitore. Se una funzionalità viene usata in più pacchetti, questo valore verrà modificato.|
|$SharePoint. Feature.FileName$|Nome del file di definizione della funzionalità contenitore, ad esempio *Feature1.feature*.|
|$SharePoint. Feature.FileNameWithoutExtension$|Nome del file di definizione della funzionalità, senza l'estensione del nome file.|
|$SharePoint. Feature.DeploymentPath$|Nome della cartella che contiene la funzionalità nel pacchetto. Questo token equivale alla proprietà "Percorso distribuzione" in Progettazione funzionalità. Un valore di esempio è "Project1_Feature1".|
|$SharePoint. Feature.Id$|ID SharePoint della funzionalità contenitore. Questo token, come con tutti i token a livello di funzionalità, può essere usato solo dai file inclusi in un pacchetto tramite una funzionalità, non aggiunti direttamente a un pacchetto all'esterno di una funzionalità.|
|$SharePoint. ProjectItem.Name$|Nome dell'elemento di progetto (non il nome del file), ottenuto **da ISharePointProjectItem.Name**.|
|$SharePoint. Digitare \<GUID> . AssemblyQualifiedName$|Nome completo di assembly del tipo che corrisponde al [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] del token. Il formato del [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] è minuscolo e corrisponde al formato Guid.ToString("D"), vale a dire xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx.|
|$SharePoint. Digitare \<GUID> . FullName$|Nome completo del tipo corrispondente al GUID nel token. Il formato del GUID è minuscolo e corrisponde al formato Guid.ToString("D") (ovvero xxxxxxxx-xxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|

## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>Aggiungere estensioni all'elenco di estensioni di file di sostituzione dei token
 Sebbene i token possano essere teoricamente usati da qualsiasi file appartenente a un elemento di progetto SharePoint incluso nel pacchetto, per impostazione predefinita cerca i token solo nei file di pacchetto, nei file manifesto e nei file con le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] estensioni seguenti:

- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]

- ASCX

- ASPX

- Webpart

- DWP

  Queste estensioni sono definite `<TokenReplacementFileExtensions>` dall'elemento nel file Microsoft.VisualStudio.SharePoint.targets, che si trova nel ... \\<cartella \> \MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools.

  È tuttavia possibile aggiungere altre estensioni di file all'elenco. Aggiungere un elemento a qualsiasi PropertyGroup nel file SharePoint progetto definito prima di `<TokenReplacementFileExtensions>` \<Import> del file SharePoint targets.

> [!NOTE]
> Poiché la sostituzione dei token si verifica dopo la compilazione di un progetto, è consigliabile non aggiungere estensioni di file per i tipi di file compilati, ad esempio *cs,* *vb* *o resx.* I token vengono sostituiti solo nei file non compilati.

 Ad esempio, per aggiungere le estensioni di file (*.myextension* e *.yourextension*) all'elenco di estensioni di file di sostituzione dei token, è necessario aggiungere quanto segue a un file di progetto (con estensione *csproj):*

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

 È possibile aggiungere l'estensione direttamente al file delle destinazioni *(con estensione targets).* Tuttavia, l'aggiunta dell'estensione modifica l'elenco delle estensioni per SharePoint i progetti in pacchetto nel sistema locale, non solo per i propri progetti. Questa estensione può essere utile quando si è l'unico sviluppatore del sistema o se la maggior parte dei progetti la richiede. Tuttavia, poiché è specifico del sistema, questo approccio non è portabile ed è quindi consigliabile aggiungere estensioni al file di progetto.

## <a name="see-also"></a>Vedi anche
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
