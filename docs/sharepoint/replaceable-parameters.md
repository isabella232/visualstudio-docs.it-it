---
title: Parametri sostituibili | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload: office
ms.openlocfilehash: e79442ea42583f326f9cb59360777269c399b7a0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879298"
---
# <a name="replaceable-parameters"></a>Parametri sostituibili
  Parametri sostituibili, oppure *token*, può essere usato nei file di progetto per fornire valori per elementi di soluzione SharePoint con i valori effettivi non sono noti in fase di progettazione. Si tratta di una funzione simile allo standard [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] token del modello. Per altre informazioni, vedere [parametri di modello](/visualstudio/ide/template-parameters).  
  
## <a name="token-format"></a>Formato del token
 Token iniziano e terminano con un simbolo di dollaro ($). Nella distribuzione, eventuali token usati vengono sostituiti con i valori effettivi quando viene incluso nel pacchetto di un progetto in un pacchetto di soluzione SharePoint (*wsp* file). Ad esempio, il token **$SharePoint.Package.Name$** potrebbe essere risolto per la stringa "Test SharePoint Package".  
  
## <a name="token-rules"></a>Regole di token
 Le regole seguenti si applicano ai token:  
  
- I token possono essere specificati in qualsiasi punto in una riga.  
  
- I token non possono estendersi su più righe.  
  
- Lo stesso token può essere specificato più volte sulla stessa riga e nello stesso file.  
  
- Token diversi può essere specificato nella stessa riga.  
  
  I token che non seguono queste regole vengono ignorati e non generano un avviso o errore.  
  
  La sostituzione dei token con valori di stringa viene eseguita immediatamente dopo la trasformazione del manifesto. Questa sostituzione consente all'utente di modificare i modelli con i token del manifesto.  
  
### <a name="token-name-resolution"></a>Risoluzione dei nomi di token
 Nella maggior parte dei casi, un token viene risolto in un valore specifico indipendentemente da dove è contenuto. Tuttavia, se il token è correlato a un pacchetto o una funzionalità, il valore del token dipende in cui è contenuto. Ad esempio, se è una funzionalità nel pacchetto, il token `$SharePoint.Package.Name$` risolve nel valore di "Pacchetto r." Se la stessa funzionalità è nel pacchetto B, allora `$SharePoint.Package.Name$` si risolve in "Del pacchetto B."  
  
## <a name="tokens-list"></a>Elenco token
 La tabella seguente elenca i token disponibili.  
  
|nome|Descrizione|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|Il nome dell'oggetto contenitore, ad esempio, file, progetto *NewProj*.|  
|$SharePoint.Project.FileNameWithoutExtension$|Il nome del file di progetto contenitore senza l'estensione del nome file. Ad esempio, "NewProj".|  
|$SharePoint.Project.AssemblyFullName$|Il nome visualizzato (nome sicuro) del progetto che lo contiene dell'assembly di output.|  
|$SharePoint.Project.AssemblyFileName$|Il nome del progetto che contiene dell'assembly di output.|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|Il nome del progetto che contiene dell'assembly, senza l'estensione del nome file di output.|  
|$SharePoint.Project.AssemblyPublicKeyToken$|Assembly, convertito in una stringa di output del token di chiave pubblica del progetto che lo contiene. (16 caratteri in "x2" formato esadecimale.)|  
|$SharePoint.Package.Name$|Il nome del pacchetto che lo contiene.|  
|$SharePoint.Package.FileName$|Nome del file di definizione del pacchetto che lo contiene.|  
|$SharePoint.Package.FileNameWithoutExtension$|Il nome (senza estensione) del file di definizione del pacchetto che lo contiene.|  
|$SharePoint.Package.Id$|L'ID di SharePoint per il pacchetto che lo contiene. Se una funzionalità viene usata in più pacchetti, questo valore verrà modificato.|  
|$SharePoint.Feature.FileName$|Funzionalità con il nome del file di definizione dell'oggetto contenitore, ad esempio *Feature1*.|  
|$SharePoint.Feature.FileNameWithoutExtension$|Il nome del file di definizione di funzionalità, senza l'estensione del nome file.|  
|$SharePoint.Feature.DeploymentPath$|Il nome della cartella che contiene la funzionalità nel pacchetto. Questo token corrisponde alla proprietà "Percorso di distribuzione" nella finestra di progettazione di funzionalità. È un valore di esempio, "Project1_Feature1".|  
|$SharePoint.Feature.Id$|L'ID SharePoint della funzionalità che lo contiene. Questo token, come con tutti i token a livello di funzionalità, può essere usato solo per i file inclusi in un pacchetto tramite una funzionalità, non aggiunti direttamente a un pacchetto all'esterno di una funzionalità.|  
|$SharePoint.ProjectItem.Name$|Il nome dell'elemento del progetto (non il nome file), ottenuto da **ISharePointProjectItem.Name**.|  
|$SharePoint.Type. \<GUID >. $ AssemblyQualifiedName|Nome completo di assembly del tipo che corrisponde al [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] del token. Il formato del [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] è minuscolo e corrisponde al formato Guid.ToString("D"), vale a dire xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx.|  
|$SharePoint.Type. \<GUID >. $ FullName|Il nome completo del tipo che corrisponde al GUID nel token. Il formato del GUID è minuscolo e corrisponde al formato GUID (vale a dire xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
  
## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>Aggiungere le estensioni per l'elenco di estensioni di file di sostituzione dei token
 Anche se i token in teoria possono essere usati da tutti i file che appartiene a un elemento incluso nel pacchetto, per impostazione predefinita, un progetto SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ricerche per i token solo nel file di pacchetto, i file manifesto e i file con le estensioni seguenti:  
  
- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
- ASCX  
  
- ASPX  
  
- Web part  
  
- CON ESTENSIONE DWP  
  
  Queste estensioni sono definite dal `<TokenReplacementFileExtensions>` elemento nel file targets, che si trova nel... \\< file di programma\>\MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools cartella.  
  
  È tuttavia possibile aggiungere altre estensioni di file all'elenco. Aggiungere un `<TokenReplacementFileExtensions>` elemento a qualsiasi oggetto PropertyGroup nel file di progetto SharePoint definito prima il \<Import > del file di destinazioni di SharePoint.  
  
> [!NOTE]  
>  Poiché la sostituzione dei token si verifica dopo la compilazione di un progetto, non è possibile aggiungere estensioni di file per i tipi di file che vengono compilati, ad esempio *cs*, *vb* oppure *resx*. I token vengono sostituiti solo nei file non compilati.  
  
 Ad esempio, per aggiungere le estensioni del nome file (*MyExtension* e *yourextension*) all'elenco di estensioni di file di sostituzione dei token, aggiungere quanto segue a un progetto (*csproj* ) file:  
  
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
  
 È possibile aggiungere l'estensione direttamente alle destinazioni (*targets*) file. Tuttavia, non aggiungere l'estensione viene modificato l'elenco di estensioni per tutti i progetti SharePoint incluso nel pacchetto nel sistema locale, solo il proprio. Questa estensione può essere utile quando si è l'unico sviluppatore del sistema o se richiedono la maggior parte dei progetti. Tuttavia, poiché è specifico del sistema, questo approccio non è portabile e di conseguenza, è consigliabile che si aggiungere tutte le estensioni al file di progetto.  
  
## <a name="see-also"></a>Vedere anche
 [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
