---
title: 'Procedura: Creare modelli di progetto | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- Visual Studio templates, creating project templates
- project templates, metadata files
- Visual Studio templates, project templates
- project templates, custom template locations
- project templates, creating
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e7e8efd905667c235d80d64e1c7ca7660281a9ea
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527141"
---
# <a name="how-to-create-project-templates"></a>Procedura: creare modelli di progetto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: creare modelli di progetto](https://docs.microsoft.com/visualstudio/ide/how-to-create-project-templates).  
  
Questa procedura consente di creare un modello tramite l'**Esportazione guidata modelli**, che crea il pacchetto del modello in un file con estensione zip. Per una distribuzione più efficiente, è anche possibile creare modelli in formato VSIX tramite l'estensione Esportazione guidata modelli o con i modelli inclusi in [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]. In alternativa è possibile creare modelli manualmente.  
  
### <a name="to-create-a-custom-project-template-with-the-standard-export-template-wizard"></a>Per creare un modello di progetto personalizzato con l'Esportazione guidata modelli standard  
  
1.  Creare un progetto.  
  
    > [!NOTE]
    >  Quando si assegna il nome a un progetto che fungerà da origine per un modello, usare solo caratteri di identificatore validi. Un modello esportato da un progetto con nome contenente caratteri non validi può causare errori di compilazione nei progetti futuri basati sul modello. Per altre informazioni sui caratteri di identificatore valido, vedere [Declared Element Names](http://msdn.microsoft.com/library/09d8843b-c0dc-4afe-9dab-87c439a69e66) (Nomi di elementi dichiarati).  
  
2.  Modificare il progetto finché non è pronto per l'esportazione come modello.  
  
3.  Modificare in base alle esigenze i file del codice per indicare dove deve essere applicata la sostituzione dei parametri. Per altre informazioni sulla sostituzione dei parametri, vedere [Procedura: Sostituire i parametri di un modello](../ide/how-to-substitute-parameters-in-a-template.md).  
  
4.  Nel menu **File** scegliere**Esporta modello**. Verrà aperta l'**Esportazione guidata modelli**.  
  
5.  Fare clic su **Modello di progetto**.  
  
6.  Se la soluzione corrente contiene più progetti, selezionare i progetti da esportare in un modello.  
  
7.  Scegliere **Avanti**.  
  
8.  Selezionare un'icona e un'immagine di anteprima per il modello. Queste verranno visualizzate nella finestra di dialogo **Nuovo progetto**.  
  
9. Immettere un nome e una descrizione per il modello.  
  
10. Scegliere **Fine**. Il progetto verrà esportato in un file con estensione zip, inserito nel percorso di output specificato e, se questa azione è stata selezionata, importato in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     Se [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] è installato, è possibile eseguire il wrapping del modello finito in un file con estensione vsix per la distribuzione tramite il modello **Progetto VSIX**. Per altre informazioni, vedere [Introduzione al modello di progetto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Procedura: Creare modelli di elementi](../ide/how-to-create-item-templates.md)



