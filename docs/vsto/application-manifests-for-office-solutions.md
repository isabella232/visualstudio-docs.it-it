---
title: Manifesti dell'applicazione per Office soluzioni
description: Informazioni su come un manifesto dell'applicazione è un file XML che descrive gli assembly caricati in una Microsoft Office soluzione.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 2e7150adfe0c3480de65acbdaa0e26f4b33effb4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038279"
---
# <a name="application-manifests-for-office-solutions"></a>Manifesti dell'applicazione per Office soluzioni
  Un manifesto dell'applicazione è un file XML che descrive gli assembly caricati in una soluzione Microsoft Office. Gli Microsoft Office di sviluppo in Visual Studio lo schema del manifesto dell'applicazione definito nel ClickOnce del manifesto [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] [dell'applicazione.](../deployment/clickonce-application-manifest.md)

 I manifesti dell'applicazione delle soluzioni Office usano gli elementi e gli attributi [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] seguenti.

|Elemento|Descrizione|Attributi|
|-------------|-----------------|----------------|
|[&#60;assembly&#62;'&#40;ClickOnce'&#41;](../deployment/assembly-element-clickonce-deployment.md)|Obbligatorio. Elemento di primo livello.|**manifestVersion**|
|[&#60;assemblyIdentity&#62; Element &#40;ClickOnce Application&#41;](../deployment/assemblyidentity-element-clickonce-deployment.md)|Obbligatorio. Identifica l'assembly primario dell'applicazione [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .|**nome**<br /><br /> **version**<br /><br /> **Publickeytoken**<br /><br /> **processorArchitecture**<br /><br /> **language**|
|[&#60;trustInfo&#62;'&#40;ClickOnce'&#41;](../deployment/trustinfo-element-clickonce-application.md)|Identifica i requisiti di sicurezza dell'applicazione.|Nessuno|
|[&#60;entryPoint&#62; element &#40;ClickOnce Application&#41;](../deployment/entrypoint-element-clickonce-application.md)|Obbligatorio. Identifica il punto di ingresso del codice dell'applicazione per l'esecuzione.|**nome**<br /><br /> **dependencyName**<br /><br /> **customHostSpecified**|
|[&#60;'elemento dependency&#62;'&#40;ClickOnce'&#41;](../deployment/dependency-element-clickonce-deployment.md)|Obbligatorio. Identifica ogni dipendenza necessaria per l'esecuzione dell'applicazione. Può anche identificare gli assembly che è necessario preinstallare.|Nessuno|
|[&#60;file&#62;'&#40;ClickOnce'&#41;](../deployment/file-element-clickonce-application.md)|Obbligatorio. Identifica ogni file non di assembly usato dall'applicazione. Può includere i dati sull'isolamento COM (Component Object Model) associati al file.|**nome**<br /><br /> **size**|

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
|[&#60;elemento customHostSpecified&#62; &#40;Office sviluppo in Visual Studio&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Obbligatorio. Contrassegna specificatamente il manifesto come soluzione Office.|Nessuno|
|[&#60;addin&#62; element &#40;Office Development in Visual Studio&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Obbligatorio. Archivia i punti di ingresso in un solo spazio dei nomi.|Nessuno|
|[&#60;entryPointsCollection&#62; element &#40;Office Development in Visual Studio&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Obbligatorio. Raggruppa tutti gli assembly di una o più soluzioni Office.|**id**|
|[&#60;entryPoints&#62; element &#40;Office Development in Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Obbligatorio. Raggruppa tutti gli assembly da eseguire in una soluzione Office.|Nessuno|
|[&#60;entryPoint&#62; elemento &#40;Office sviluppo in Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Obbligatorio. Identifica l'assembly da eseguire in una soluzione Office.|**class**<br /><br /> **Contratto**|
|[&#60;aggiornare&#62; elemento &#40;Office sviluppo in Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md)|Obbligatorio. Configura gli aggiornamenti per la soluzione.|**abilitata**<br /><br /> **expiration**|
|[&#60;'elemento&#62; &#40;Office postActions in Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|facoltativo. Raggruppa tutte le azioni post-distribuzione, ovvero azioni che vengono eseguite dopo l'installazione di soluzioni Office.|Nessuno|
|[&#60;elemento postAction&#62;'&#40;Office sviluppo in Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|facoltativo. Identifica un'azione post-distribuzione.|Nessuno|
|[&#60;'elemento&#62; postActionData &#40;Office sviluppo in Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|facoltativo. Configura i dati di un'azione post-distribuzione.|Nessuno|
|[&#60;'applicazione&#62; elemento &#40;Office sviluppo in Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md)|Obbligatorio. Esegue il wrapping delle informazioni specifiche dell'applicazione in un solo nodo.|Nessuno|
|[&#60;personalizzazioni&#62;'elemento &#40;Office sviluppo in Visual Studio&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Obbligatorio. Archivia le informazioni host specifiche di tutte le applicazioni in uno spazio dei nomi separato.|Nessuno|
|[&#60;personalizzazione&#62; elemento &#40;Office sviluppo in Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Obbligatorio. Archivia le informazioni host specifiche dell'applicazione in uno spazio dei nomi separato.|**xmlns**|
|[&#60;documento&#62;'&#40;Office sviluppo in Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md)|Obbligatorio solo per soluzioni a livello di documento. Archivia le informazioni specifiche della personalizzazione.|**solutionId**|
|[&#60;appAddin&#62; Element &#40;Office Development in Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Obbligatorio solo per soluzioni a livello di applicazione. Archivia le informazioni specifiche della personalizzazione.|**applicazione**<br /><br /> **Loadbehavior**<br /><br /> **Keyname**|
|[&#60;elemento friendlyName&#62;'&#40;Office in Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|facoltativo. Archivia il nome del componente aggiuntivo VSTO che viene visualizzato nell'elenco di componenti aggiuntivi VSTO installati.|Nessuno|
|[&#60;descrizione&#62; element &#40;Office Development in Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md)|Obbligatorio solo VSTO componenti aggiuntivi. Archivia la descrizione visualizzata nell'elenco dei programmi installati.|Nessuno|
|[&#60;formRegions&#62; Element &#40;Office Development in Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Obbligatorio solo per i componenti aggiuntivi VSTO di Outlook che includono aree di modulo.|Nessuno|
|[&#60;formRegion&#62; Element &#40;Office Development in Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Obbligatorio solo per i componenti aggiuntivi VSTO di Outlook che includono aree di modulo.|**Nome**|
|[&#60;'elemento&#62; vstoRuntime &#40;Office sviluppo in Visual Studio&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Obbligatorio. Descrive una versione specifica del runtime di Visual Studio Tools per Office supportata dalla soluzione Office.|**Rilascio**<br /><br /> **version**<br /><br /> **supportUrl**|

## <a name="remarks"></a>Commenti
 È possibile modificare manualmente i manifesti dell'applicazione e di distribuzione nelle soluzioni Office. Successivamente, è necessario firmare nuovamente i manifesti dell'applicazione e della distribuzione usando Strumento per la generazione e la modifica di manifesti *(* mage.exee *mageui.exe*). Per altre informazioni, vedere [Procedura: Firmare nuovamente manifesti di applicazione e distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="file-location"></a>Percorso del file
 Un manifesto dell'applicazione è specifico per una singola versione di una soluzione. Per questo motivo, i manifesti dell'applicazione devono essere archiviati separatamente da quelli di distribuzione. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] inserisce i file specifici della versione in una sottodirectory denominata in base alla versione associata nella sottodirectory *File* dell'applicazione nella cartella publish.

## <a name="file-name-syntax"></a>Sintassi del nome file
 Il nome di un file manifesto dell'applicazione deve essere il nome completo e l'estensione dell'applicazione identificati **nell'elemento assemblyIdentity,** seguiti dall'estensione *manifest*. Ad esempio, un manifesto dell'applicazione che fa riferimento *alla personalizzazioneOutlookAddIn1.dll* usa la sintassi del nome file seguente.

 `OutlookAddIn1.dll.manifest`

## <a name="see-also"></a>Vedi anche

- [Manifesti di distribuzione per Office soluzioni](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)