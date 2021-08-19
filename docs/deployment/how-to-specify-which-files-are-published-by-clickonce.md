---
title: Specificare i file da pubblicare (ClickOnce)
description: Informazioni su come escludere file, contrassegnarli come file di dati o prerequisiti e creare gruppi per l'installazione condizionale per un ClickOnce appliazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.File
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, file exclusion
- files, publishing via ClickOnce
ms.assetid: 579c134a-d50f-4e0c-8e05-2a4ff654896a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: c6fbe8b1543fdff870a0a5557c313080acd390c8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146290"
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>Procedura: Specificare i file da pubblicare mediante ClickOnce
Quando si pubblica [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione, tutti i file non di codice nel progetto vengono distribuiti insieme all'applicazione. In alcuni casi, potrebbe non essere necessario pubblicare determinati file o installare determinati file in base alle condizioni. Visual Studio offre le funzionalità per escludere i file, contrassegnarli come file di dati o prerequisiti e creare gruppi di file per l'installazione condizionale.

 I file per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione vengono gestiti nella  **finestra di** dialogo File dell'applicazione , accessibile dalla pagina Pubblica della **finestra di Project Designer**.

 Inizialmente è presente un singolo gruppo di file **denominato (Obbligatorio).** È possibile creare gruppi di file aggiuntivi e assegnare file a essi. Non è possibile modificare **il gruppo di download** per i file necessari per l'esecuzione dell'applicazione. Ad esempio, i file .exe dell'applicazione contrassegnati come file di dati devono appartenere al **gruppo (Obbligatorio).**

 Il valore dello stato di pubblicazione predefinito di un file è contrassegnato **con (Auto).** Ad esempio, lo stato di .exe'applicazione è **Includi (automatico)** per impostazione predefinita.

 I file con **la proprietà Azione di** compilazione impostata su **Contenuto** vengono designati come file dell'applicazione e verranno contrassegnati come inclusi per impostazione predefinita. Possono essere inclusi, esclusi o contrassegnati come file di dati. Le eccezioni sono le seguenti:

- I file di dati database SQL (*mdf* e *mdb*) e i file XML verranno contrassegnati come file di dati per impostazione predefinita.

- I riferimenti agli assembly *(file.dll)* vengono designati come segue quando si aggiunge il riferimento: Se Copy **Local** è **False**, è contrassegnato per impostazione predefinita come assembly prerequisito (**Prerequisite (Auto)**) che deve essere presente nella Global Assembly Cache prima dell'installazione dell'applicazione. Se **Copy Local** è **True,** l'assembly è contrassegnato per impostazione predefinita come assembly dell'applicazione **(Include (Auto)** e verrà copiato nella cartella dell'applicazione al momento dell'installazione. Un riferimento COM verrà visualizzato nella **finestra** di dialogo File dell'applicazione (come file con estensione *ocx)* solo se la relativa **proprietà Isolated** è impostata su **True.** Per impostazione predefinita, verrà incluso.

### <a name="to-add-files-to-the-application-files-dialog-box"></a>Per aggiungere file alla finestra di dialogo File applicazione

1. Selezionare un file di dati in **Esplora soluzioni**.

2. Nella finestra Finestra Proprietà modificare la **proprietà Azione di** compilazione sul **valore** Contenuto.

### <a name="to-exclude-files-from-clickonce-publishing"></a>Per escludere i file dalla ClickOnce pubblicazione

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic **sul pulsante File applicazione** per aprire la finestra di dialogo **File** applicazione .

4. Nella finestra **di dialogo File** applicazione selezionare il file da escludere.

5. Nel campo **Stato pubblicazione** selezionare **Escludi** dall'elenco a discesa.

### <a name="to-mark-files-as-data-files"></a>Per contrassegnare i file come file di dati

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic **sul pulsante File applicazione** per aprire la finestra di dialogo **File** applicazione .

4. Nella finestra **di dialogo File** applicazione selezionare il file da contrassegnare come dati.

5. Nel campo **Stato pubblicazione** selezionare File **di dati** nell'elenco a discesa.

### <a name="to-mark-files-as-prerequisites"></a>Per contrassegnare i file come prerequisiti

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic **sul pulsante File applicazione** per aprire la finestra di dialogo **File** applicazione .

4. Nella finestra **di dialogo File** applicazione selezionare l'assembly dell'applicazione *(.dll* file) da contrassegnare come prerequisito. Si noti che l'applicazione deve avere un riferimento all'assembly dell'applicazione per poter essere visualizzata nell'elenco.

5. Nel campo **Stato pubblicazione** selezionare **Prerequisito** nell'elenco a discesa.

### <a name="to-add-a-new-file-group"></a>Per aggiungere un nuovo file group

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic **sul pulsante File applicazione** per aprire la finestra di dialogo **File** applicazione .

4. Nella finestra **di dialogo File** applicazione selezionare il campo **Gruppo** per un file da includere nel nuovo gruppo.

    > [!NOTE]
    > I file devono avere la **proprietà Azione di** compilazione impostata su **Contenuto** prima che i nomi dei file vengano visualizzati nella finestra di **dialogo File** applicazione .

5. Nel campo **Download Group (Scarica** gruppo) **\<New...>** selezionare dall'elenco a discesa.

6. Nella finestra **di dialogo Nuovo** gruppo immettere un nome per il gruppo e quindi fare clic su **OK.**

### <a name="to-add-a-file-to-a-group"></a>Per aggiungere un file a un gruppo

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic **sul pulsante File applicazione** per aprire la finestra di dialogo **File** applicazione .

4. Nella finestra **di dialogo File** applicazione selezionare il campo **Gruppo** per un file da includere nel nuovo gruppo.

5. Nel campo **Download Group (Scarica** gruppo) selezionare un gruppo dall'elenco a discesa.

    > [!NOTE]
    > Non è possibile modificare **il gruppo di download** per i file necessari per l'esecuzione dell'applicazione.

## <a name="see-also"></a>Vedi anche
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: Pubblicare un'applicazione ClickOnce tramite la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)