---
title: 'Procedura: aggiornare modelli esistenti | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b56cf11057957b0eb99fc065ed26af10d8adfbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670579"
---
# <a name="how-to-update-existing-templates"></a>Procedura: aggiornare modelli esistenti
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

9. Eseguire questo comando: `devenv /installvstemplates`.

## <a name="see-also"></a>Vedere anche
 [Personalizzazione dei modelli](../ide/customizing-project-and-item-templates.md) [creazione di modelli di progetto e modelli di elemento di](../ide/creating-project-and-item-templates.md) [Visual Studio riferimenti allo schema](../extensibility/visual-studio-template-schema-reference.md) del modello [parametri](../ide/template-parameters.md) [procedura: creare starter kit](../ide/how-to-create-starter-kits.md)
