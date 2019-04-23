---
title: 'Procedura: Aggiornare modelli esistenti | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 26482e844a4850efb1c50b15e51e4153baf1f9ab
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60075996"
---
# <a name="how-to-update-existing-templates"></a>Procedura: Aggiornare modelli esistenti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dopo aver creato un modello e compresso i file in un file ZIP, può essere necessario modificare il modello. L'operazione può essere eseguita manualmente cambiando i file nel modello oppure esportando un nuovo modello da un progetto basato sul modello.  
  
## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>Uso dell'Esportazione guidata modelli per aggiornare un modello esistente  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] offre l'**Esportazione guidata modelli** che può essere usata per aggiornare un modello esistente.  
  
#### <a name="to-use-export-template-to-update-an-existing-template"></a>Per usare l'Esportazione guidata modelli per aggiornare un modello esistente  
  
1. Scegliere **Nuovo** dal menu **File** , quindi **Nuovo progetto**.  
  
2. Selezionare il modello da aggiornare, specificare un nome e un percorso per il progetto temporaneo, quindi fare clic su **OK**.  
  
3. Modificare il progetto in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4. Scegliere **Esporta modello** dal menu **File** e usare l' **Esportazione guidata modelli** per creare un nuovo modello.  
  
5. Dopo aver compresso il modello aggiornato in un file con estensione zip, eliminare il file ZIP del modello precedente.  
  
## <a name="manually-updating-an-existing-template"></a>Aggiornamento manuale di un modello esistente  
 È possibile aggiornare un modello esistente al di fuori di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modificando i file inclusi nel file compresso con estensione zip.  
  
#### <a name="to-manually-update-an-existing-template"></a>Per aggiornare manualmente un modello esistente  
  
1. Individuare il file ZIP che contiene il modello. Per impostazione predefinita questo file si trova in Documenti\Visual Studio *Versione*\My Exported Templates\\.  
  
2. Estrarre il file ZIP.  
  
3. Modificare o eliminare i file del modello corrente o aggiungere nuovi file al modello.  
  
4. Aprire, modificare e salvare il file XML con estensione vstemplate per gestire il nuovo comportamento o i nuovi file. Per altre informazioni sullo schema con estensione vstemplate, vedere [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md). Per altre informazioni sugli elementi che è possibile parametrizzare nei file di origine, vedere [Parametri di modelli](../ide/template-parameters.md)  
  
5. Selezionare i file inclusi nel modello, fare clic con il pulsante destro del mouse e scegliere **Invia a**, quindi **Cartella compressa**. I file selezionati verranno compressi in un file ZIP.  
  
6. Inserire il nuovo file ZIP nella stessa directory del vecchio file ZIP.  
  
7. Eliminare i file di modello estratti e il vecchio file di modello ZIP.  
  
8. Avviare come amministratore un'istanza del prompt dei comandi di sviluppo (nel menu Start in **Visual Studio 2010/Strumenti di Visual Studio/Prompt dei comandi per gli sviluppatori**).  
  
9. Eseguire il comando seguente: `devenv /installvstemplates`.  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione di modelli](../ide/customizing-project-and-item-templates.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Parametri di modello](../ide/template-parameters.md)   
 [Procedura: Creare starter kit](../ide/how-to-create-starter-kits.md)
