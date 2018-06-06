---
title: Creazione di pacchetti delle soluzioni SharePoint | Documenti Microsoft
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
ms.openlocfilehash: 957789c4adfc476429179ed84f87f544c0d37143
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765271"
---
# <a name="create-sharepoint-solution-packages"></a>Creare pacchetti di soluzioni SharePoint
  Utilizzando la finestra di progettazione del pacchetto, è possibile creare e personalizzare i pacchetti di distribuzione. Ad esempio, è possibile aggiungere elementi di progetto SharePoint e le funzionalità, reimpostare il server IIS, impostare gli ambiti di attivazione di funzionalità e identificare le dipendenze di funzionalità. Inoltre, la finestra di progettazione genera un manifesto del file XML che descrive ogni pacchetto.  
  
## <a name="packaging-tools"></a>Strumenti di creazione di pacchetti
 È possibile utilizzare il **Progettazione pacchetti** per personalizzare il pacchetto e generare il manifesto. È possibile includere elementi di progetto SharePoint, configurare se il server Web deve essere reimpostato e impostare il tipo di server di distribuzione. Per ulteriori informazioni, vedere [procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto utilizzando la finestra di progettazione del pacchetto](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
 In alternativa, è possibile utilizzare il **Esplora pacchetti** per modificare le funzionalità e gli elementi del file di pacchetto (*con estensione wsp*). Per ulteriori informazioni, vedere [procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto utilizzando Esplora pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
 È possibile utilizzare MSBuild e Visual Studio per creare pacchetto (*wsp*) i file per distribuire la soluzione di SharePoint. Questo processo genera i file di manifesto necessari per la distribuzione di SharePoint. Per ulteriori informazioni, vedere [procedura: creare un pacchetto di SharePoint](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b) e [procedura: creare un pacchetto della soluzione SharePoint tramite attività MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).  
  
## <a name="package-designer-options"></a>Opzioni di progettazione pacchetti
 Nella tabella seguente vengono illustrate le proprietà che è possibile personalizzare nei pacchetti di SharePoint con il **Progettazione pacchetti**.  
  
|Proprietà della finestra di progettazione del pacchetto|Descrizione dell'impostazione predefinita|  
|-------------------------------|------------------------------------|  
|nome|Obbligatorio. Il nome predefinito del pacchetto è impostato su *ProjectName*.|  
|Server Web di reimpostazione|Facoltativo. Selezionare se si desidera riavviare il server Web dopo il *wsp* file viene installato nel server SharePoint.|  
|Tipo di Server di distribuzione|Obbligatorio. Per impostazione predefinita, l'ambito è impostato su ApplicationServer.<br /><br /> Server applicazioni: Descrive un server che ospita i servizi.<br /><br /> WebFrontEnd: Descrive un server che ospita i siti Web.|  
|Elementi nella soluzione|Tutti gli elementi di progetto SharePoint e le funzionalità che possono essere aggiunto al pacchetto.|  
|Elementi nel pacchetto|Facoltativo. Tutti gli elementi di SharePoint e le funzionalità che si desidera distribuire nel pacchetto.|  
  
## <a name="configure-the-packaging-process"></a>Configurare il processo di creazione di pacchetti
 Dopo aver sviluppato le soluzioni SharePoint in Visual Studio, è possibile personalizzare la modalità in cui sono inclusi i progetti.  
  
 Nella tabella seguente vengono visualizzate le due destinazioni di MSBuild che è possibile utilizzare per personalizzare il modo in cui *wsp* file viene creato.  
  
|destinazione|Descrizione|  
|------------|-----------------|  
|Destinazioni di BeforeLayout|La destinazione che esegue le attività immediatamente prima che i file vengono copiati in una directory intermedia. È possibile modificare i file prima di creare un file di pacchetto (*wsp*).|  
|AfterLayout|La destinazione che esegue le attività immediatamente dopo che i file vengono copiati in una directory intermedia.|  
  
 Per ulteriori informazioni, [procedura: personalizzare un pacchetto di soluzione SharePoint tramite utilizzando le destinazioni di MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).  
  
## <a name="packaging-architecture"></a>Architettura dei pacchetti
 I passaggi seguenti si verificano quando si crea un pacchetto di SharePoint (*wsp*) in Visual Studio.  
  
1.  La funzionalità e i pacchetti vengono convalidati per assicurarsi che la struttura fisica e semantica del pacchetto sia corretta.  
  
2.  La funzionalità, gli elementi di progetto e file del pacchetto nel pacchetto sono enumerati. File manifesto per i pacchetti e le funzionalità vengono trasformati in modo da includere tutte le informazioni necessarie per la distribuzione e attivazione. I token vengono sostituiti con il valore completo.  
  
3.  Viene eseguita la destinazione BeforeLayout MSBuild personalizzabile. È possibile creare questo passaggio per apportare qualsiasi modifica personalizzata per il pacchetto prima la *wsp* file viene creato.  
  
4.  I file enumerati vengono copiati in una directory intermedia.  
  
5.  Viene eseguita la destinazione MSBuild AfterLayout personalizzabile. È possibile creare questo passaggio per apportare qualsiasi modifica personalizzata per il pacchetto prima la *wsp* file viene creato.  
  
6.  I file nella directory intermedia vengono aggiunti per il *wsp* file.  
  
## <a name="package-folder-structure"></a>Struttura delle cartelle del pacchetto
 Quando si crea il pacchetto del progetto SharePoint, un *wsp* viene creato automaticamente nel file il *ConfigurazioneBuild\{BuildConfiguration}* cartella. Se, ad esempio, la soluzione sia *C:\Visual Studio 2013\Projects\ListDefinition1* e la configurazione della build è impostata su Release, la *con estensione wsp* file si trova nella *2013\ C:\Visual Studio Projects\ListDefinition1\bin\Release*.  
  
## <a name="see-also"></a>Vedere anche
 [Procedura: Personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [Procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Progettazione pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)   
 [Procedura: creare un pacchetto di SharePoint](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)   
 [Procedura: creare un pacchetto della soluzione SharePoint tramite le attività di MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [Procedura: Personalizzare un pacchetto della soluzione SharePoint tramite le destinazioni di MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)  
  
 