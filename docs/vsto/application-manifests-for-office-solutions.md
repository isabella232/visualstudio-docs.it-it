---
title: Manifesti dell'applicazione per le soluzioni Office
description: Informazioni sul modo in cui un manifesto dell'applicazione è un file XML che descrive gli assembly caricati in una soluzione Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b3fbea6df2b66a108a048332e28a623bdaa95786
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839028"
---
# <a name="application-manifests-for-office-solutions"></a>Manifesti dell'applicazione per le soluzioni Office
  Un manifesto dell'applicazione è un file XML che descrive gli assembly caricati in una soluzione Microsoft Office. Gli strumenti di sviluppo Microsoft Office in Visual Studio usano lo [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] schema del manifesto dell'applicazione definito nel riferimento del [manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md) .

 I manifesti dell'applicazione delle soluzioni Office usano gli elementi e gli attributi [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] seguenti.

|Elemento|Descrizione|Attributi|
|-------------|-----------------|----------------|
|[&#60;elemento&#62; assembly &#40;applicazione ClickOnce&#41;](../deployment/assembly-element-clickonce-deployment.md)|Obbligatorio. Elemento di primo livello.|**manifestVersion**|
|[&#60;elemento&#62; assemblyIdentity &#40;applicazione ClickOnce&#41;](../deployment/assemblyidentity-element-clickonce-deployment.md)|Obbligatorio. Identifica l'assembly primario dell'applicazione [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .|**nome**<br /><br /> **version**<br /><br /> **publicKeyToken**<br /><br /> **processorArchitecture**<br /><br /> **language**|
|[&#60;elemento&#62; trustInfo &#40;applicazione ClickOnce&#41;](../deployment/trustinfo-element-clickonce-application.md)|Identifica i requisiti di sicurezza dell'applicazione.|nessuno|
|[&#60;elemento&#62; entryPoint &#40;applicazione ClickOnce&#41;](../deployment/entrypoint-element-clickonce-application.md)|Obbligatorio. Identifica il punto di ingresso del codice dell'applicazione per l'esecuzione.|**nome**<br /><br /> **dependencyname**<br /><br /> **customHostSpecified**|
|[&#60;elemento&#62; Dependency &#40;applicazione ClickOnce&#41;](../deployment/dependency-element-clickonce-deployment.md)|Obbligatorio. Identifica ogni dipendenza necessaria per l'esecuzione dell'applicazione. Può anche identificare gli assembly che è necessario preinstallare.|nessuno|
|[&#60;elemento&#62; file &#40;applicazione ClickOnce&#41;](../deployment/file-element-clickonce-application.md)|Obbligatorio. Identifica ogni file non di assembly usato dall'applicazione. Può includere i dati sull'isolamento COM (Component Object Model) associati al file.|**nome**<br /><br /> **size**|

 I manifesti dell'applicazione delle soluzioni Office contengono l'elemento seguente nello spazio dei nomi `co.v1` .

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

 Questi manifesti dell'applicazione contengono anche gli elementi e gli attributi seguenti nello spazio dei nomi `vstav3` .

```xml
<addIn>
  <entryPointsCollection>
    <entryPoints>
      <entryPoint>
      </entryPoint>
    </entryPoints>
  </entryPointsCollection>
  <update></update>
  <postActions>
    <postAction>
      <postActionData>
      </postActionData>
    <postAction>
  </postActions>
  <application>
    <customizations>
      <customization>
      </customization>
    </customizations>
  </application
</addIn>
```

|Elemento|Descrizione|Attributi|
|-------------|-----------------|----------------|
|[&#60;customHostSpecified&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Obbligatorio. Contrassegna specificatamente il manifesto come soluzione Office.|nessuno|
|[&#60;elemento&#62; AddIn &#40;sviluppo per Office in Visual Studio&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Obbligatorio. Archivia i punti di ingresso in un solo spazio dei nomi.|nessuno|
|[&#60;entryPointsCollection&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Obbligatorio. Raggruppa tutti gli assembly di una o più soluzioni Office.|**id**|
|[&#60;entryPoints&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Obbligatorio. Raggruppa tutti gli assembly da eseguire in una soluzione Office.|nessuno|
|[&#60;elemento&#62; entryPoint &#40;sviluppo per Office in Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Obbligatorio. Identifica l'assembly da eseguire in una soluzione Office.|**class**<br /><br /> **contratto**|
|[&#60;aggiornare&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md)|Obbligatorio. Configura gli aggiornamenti per la soluzione.|**abilitato**<br /><br /> **expiration**|
|[&#60;le postazioni&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|facoltativo. Raggruppa tutte le azioni post-distribuzione, ovvero azioni che vengono eseguite dopo l'installazione di soluzioni Office.|nessuno|
|[&#60;elemento&#62; postAction &#40;sviluppo per Office in Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|facoltativo. Identifica un'azione post-distribuzione.|nessuno|
|[&#60;postActionData&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|facoltativo. Configura i dati di un'azione post-distribuzione.|nessuno|
|[&#60;elemento&#62; dell'applicazione &#40;sviluppo per Office in Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md)|Obbligatorio. Esegue il wrapping delle informazioni specifiche dell'applicazione in un solo nodo.|nessuno|
|[&#60;le personalizzazioni&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Obbligatorio. Archivia le informazioni host specifiche di tutte le applicazioni in uno spazio dei nomi separato.|nessuno|
|[&#60;&#62; di personalizzazione elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Obbligatorio. Archivia le informazioni host specifiche dell'applicazione in uno spazio dei nomi separato.|**xmlns**|
|[&#60;elemento&#62; documento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md)|Obbligatorio solo per soluzioni a livello di documento. Archivia le informazioni specifiche della personalizzazione.|**solutionId**|
|[&#60;appAddin&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Obbligatorio solo per soluzioni a livello di applicazione. Archivia le informazioni specifiche della personalizzazione.|**applicazione**<br /><br /> **loadBehavior**<br /><br /> **keyName**|
|[ Elemento&#62;&#60;FriendlyName &#40;sviluppo per Office in Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|facoltativo. Archivia il nome del componente aggiuntivo VSTO che viene visualizzato nell'elenco di componenti aggiuntivi VSTO installati.|nessuno|
|[&#60;Description&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md)|Obbligatorio solo per i componenti aggiuntivi VSTO. Archivia la descrizione che viene visualizzata nell'elenco dei programmi installati.|nessuno|
|[&#60;formRegions&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Obbligatorio solo per i componenti aggiuntivi VSTO di Outlook che includono aree di modulo.|nessuno|
|[&#60;formRegion&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Obbligatorio solo per i componenti aggiuntivi VSTO di Outlook che includono aree di modulo.|**Nome**|
|[&#60;vstoRuntime&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Obbligatorio. Descrive una versione specifica del runtime di Visual Studio Tools per Office supportata dalla soluzione Office.|**versione**<br /><br /> **version**<br /><br /> **supportUrl**|

## <a name="remarks"></a>Commenti
 È possibile modificare manualmente i manifesti dell'applicazione e di distribuzione nelle soluzioni Office. Successivamente, è necessario firmare di nuovo i manifesti dell'applicazione e della distribuzione usando il Strumento per la generazione e la modifica di manifesti (*mage.exe* e *mageui.exe*). Per altre informazioni, vedere [Procedura: Firmare nuovamente manifesti di applicazione e distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="file-location"></a>Percorso del file
 Un manifesto dell'applicazione è specifico per una singola versione di una soluzione. Per questo motivo, i manifesti dell'applicazione devono essere archiviati separatamente da quelli di distribuzione. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] inserisce i file specifici della versione in una sottodirectory denominata in base alla versione associata nella sottodirectory *file applicazione* nella cartella di pubblicazione.

## <a name="file-name-syntax"></a>Sintassi del nome file
 Il nome di un file manifesto dell'applicazione deve essere il nome completo e l'estensione dell'applicazione come identificato nell'elemento **assemblyIdentity** , seguito dal file Extension *. manifest*. Ad esempio, un manifesto dell'applicazione che fa riferimento alla personalizzazione di *OutlookAddIn1.dll* utilizzerebbe la sintassi del nome file seguente.

 `OutlookAddIn1.dll.manifest`

## <a name="see-also"></a>Vedi anche

- [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)