---
title: 'Procedura: Aggiornare modelli esistenti | Microsoft Docs'
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 28ae63c6dba9d352025d5c87d838772a81cf989d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-update-existing-templates"></a>Procedura: Aggiornare modelli esistenti
Dopo aver creato un modello e compresso i file in un file ZIP, può essere necessario modificare il modello. L'operazione può essere eseguita manualmente cambiando i file nel modello oppure esportando un nuovo modello da un progetto basato sul modello.  
  
## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>Uso dell'Esportazione guidata modelli per aggiornare un modello esistente  
In Visual Studio è disponibile l'**Esportazione guidata modelli** che è possibile usare per aggiornare un modello esistente.  
  
#### <a name="to-use-export-template-to-update-an-existing-template"></a>Per usare l'Esportazione guidata modelli per aggiornare un modello esistente  
  
1.  Aprire la finestra di dialogo **Nuovo progetto** scegliendo **File**, **Nuovo**, **Progetto**.  
  
2.  Selezionare il modello da aggiornare, specificare un nome e un percorso per il progetto, quindi fare clic su **OK**.  
  
3.  Modificare il progetto in Visual Studio.  
  
4.  Nel menu **Progetto** scegliere**Esporta modello**.  

    Viene aperta l'**Esportazione guidata modelli**.  

5.  Seguire le istruzioni della procedura guidata per esportare il modello come file con estensione zip.  

6.  Eliminare il file di modello precedente con estensione zip.  
  
## <a name="manually-updating-an-existing-template"></a>Aggiornamento manuale di un modello esistente  
È possibile aggiornare un modello esistente all'esterno di Visual Studio modificando i file inclusi nel file compresso con estensione zip.  
  
#### <a name="to-manually-update-an-existing-template"></a>Per aggiornare manualmente un modello esistente  
  
1.  Individuare il file ZIP che contiene il modello. Per impostazione predefinita, il file si trova in %USERPROFILE%\Documents\Visual Studio \<versione\>\My Exported Templates\.  
  
2.  Estrarre il file ZIP.  
  
3.  Modificare o eliminare i file del modello corrente o aggiungere nuovi file al modello.  
  
4.  Aprire, modificare e salvare il file XML con estensione vstemplate per gestire il nuovo comportamento o i nuovi file.  

    Per altre informazioni sullo schema con estensione vstemplate, vedere [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md). Per altre informazioni sugli elementi che è possibile parametrizzare nei file di origine, vedere [Parametri di modelli](../ide/template-parameters.md).  
  
5.  Selezionare i file nel modello, fare clic con il pulsante destro del mouse e scegliere **Invia a**, quindi **Cartella compressa**.  

    I file selezionati verranno compressi in un file ZIP.  
  
6.  Inserire il nuovo file ZIP nella stessa directory del vecchio file ZIP.  
  
7.  Eliminare i file di modello estratti e il vecchio file di modello ZIP.  
  
8.  Avviare un'istanza con privilegi elevati del prompt dei comandi per gli sviluppatori:  

  1. Fare clic sul pulsante Start, scegliere **Visual Studio \<versione\>**, **Prompt dei comandi per gli sviluppatori**.  

  2. Fare clic con il pulsante destro del mouse e scegliere **Altro**, **Esegui come amministratore** dal menu di scelta rapida.  
  
9. Eseguire il comando seguente: `devenv /installvstemplates`.  
  
## <a name="see-also"></a>Vedere anche  
[Personalizzazione di modelli](../ide/customizing-project-and-item-templates.md)   
[Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
[Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
[Parametri di modello](../ide/template-parameters.md)   
[Procedura: Creare starter kit](../ide/how-to-create-starter-kits.md)