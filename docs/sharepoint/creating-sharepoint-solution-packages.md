---
title: Creazione di pacchetti delle soluzioni SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 87b80d7c607cf4de686e601263bcb67dcc2f92ae
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326852"
---
# <a name="create-sharepoint-solution-packages"></a>Creare pacchetti delle soluzioni SharePoint
  Usando la finestra di progettazione del pacchetto, è possibile creare e personalizzare i pacchetti di distribuzione. Ad esempio, è possibile aggiungere elementi di progetto SharePoint e le funzionalità, ripristinare il server IIS, impostare gli ambiti di attivazione di funzionalità e identificare le dipendenze delle funzionalità. La finestra di progettazione genera anche un manifesto, un file XML che descrive ogni pacchetto.  
  
## <a name="packaging-tools"></a>Strumenti di creazione di pacchetti
 È possibile usare la **Progettazione pacchetti** per personalizzare il pacchetto e generare il manifesto. È possibile includere elementi di progetto SharePoint, configurare se il server Web deve essere reimpostato e impostare il tipo di server di distribuzione. Per altre informazioni, vedere [procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Progettazione pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
 In alternativa, è possibile usare la **Esplora pacchetti** per modificare le funzionalità e gli elementi nel file del pacchetto (*wsp*). Per altre informazioni, vedere [procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto usando Esplora pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
 È possibile usare Visual Studio e MSBuild per creare pacchetto (*wsp*) i file per distribuire la soluzione di SharePoint. Questo processo genera file manifesto necessari per la distribuzione di SharePoint. Per altre informazioni, vedere [procedura: creare un pacchetto della soluzione SharePoint tramite le attività di MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).  
  
## <a name="package-designer-options"></a>Opzioni della finestra di progettazione di pacchetti
 Nella tabella seguente vengono illustrate le proprietà che è possibile personalizzare nei pacchetti di SharePoint con il **Progettazione pacchetti**.  
  
|Proprietà della finestra di progettazione del pacchetto|Descrizione dell'impostazione predefinita|  
|-------------------------------|------------------------------------|  
|nome|Obbligatorio. Il nome predefinito del pacchetto è impostato su *ProjectName*.|  
|Reimposta server Web|Facoltativo. Selezionare se si desidera riavviare il server Web dopo il *wsp* file viene installato nel server SharePoint.|  
|Tipo di Server di distribuzione|Obbligatorio. Per impostazione predefinita, l'ambito è impostato per server applicazioni.<br /><br /> Server applicazioni: Viene descritto un server che ospita i servizi.<br /><br /> WebFrontEnd: Viene descritto un server che ospita i siti Web.|  
|Elementi nella soluzione|Tutti gli elementi di progetto SharePoint e le funzionalità che possono essere aggiunti al pacchetto.|  
|Elementi nel pacchetto|Facoltativo. Tutti gli elementi di SharePoint e le funzionalità che si desidera distribuire il pacchetto.|  
  
## <a name="configure-the-packaging-process"></a>Configurare il processo di creazione di pacchetti
 Dopo aver sviluppato le soluzioni di SharePoint in Visual Studio, è possibile personalizzare la modalità in cui sono inclusi i progetti.  
  
 La tabella seguente illustra le due destinazioni di MSBuild che è possibile usare per personalizzare il *wsp* file viene creato.  
  
|destinazione|Descrizione|  
|------------|-----------------|  
|BeforeLayout|La destinazione che esegue le attività immediatamente prima che i file vengono copiati in una directory intermedia. È possibile modificare i file prima di creare un file di pacchetto (*wsp*).|  
|AfterLayout|La destinazione che esegue le attività immediatamente dopo che i file vengono copiati in una directory intermedia.|  
  
 Per altre informazioni, [procedura: personalizzare un pacchetto della soluzione SharePoint tramite le destinazioni di MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).  
  
## <a name="packaging-architecture"></a>Architettura dei pacchetti
 I passaggi seguenti si verificano quando si crea un pacchetto di SharePoint (*wsp*) in Visual Studio.  
  
1.  Le funzionalità e i pacchetti vengono convalidati per assicurarsi che la struttura fisica e semantica del pacchetto sia corretta.  
  
2.  Vengono enumerati le funzionalità, gli elementi del progetto e file del pacchetto nel pacchetto. I file manifesto per le caratteristiche e i pacchetti vengono trasformati in modo da includere tutte le informazioni necessarie per la distribuzione e attivazione. I token vengono sostituiti con il valore completo.  
  
3.  Viene eseguita la destinazione di MSBuild di BeforeLayout personalizzabile. È possibile creare questo passaggio per apportare qualsiasi modifica personalizzata per il pacchetto prima la *wsp* file viene creato.  
  
4.  I file enumerati vengono copiati in una directory intermedia.  
  
5.  Viene eseguita la destinazione di MSBuild AfterLayout personalizzabile. È possibile creare questo passaggio per apportare qualsiasi modifica personalizzata per il pacchetto prima la *wsp* file viene creato.  
  
6.  I file nella directory intermedia vengono aggiunti per il *wsp* file.  
  
## <a name="package-folder-structure"></a>Struttura delle cartelle del pacchetto
 Quando si crea un pacchetto del progetto SharePoint, un *wsp* viene creato automaticamente nel file la *ConfigurazioneBuild\\\<BuildConfiguration >* cartella. Ad esempio, se la soluzione è *C:\Visual Studio 2013\Projects\ListDefinition1* e la configurazione di compilazione è impostata su versione, il *wsp* file si trova in *2013\ C:\Visual Studio Projects\ListDefinition1\bin\Release*.  
  
## <a name="see-also"></a>Vedere anche
 [Procedura: personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [Procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Progettazione pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)   
 [Procedura: creare un pacchetto della soluzione SharePoint tramite le attività di MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [Procedura: creare un pacchetto della soluzione SharePoint tramite le attività di MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [Procedura: personalizzare un pacchetto della soluzione SharePoint tramite le destinazioni di MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)  
  
 
