---
title: 'Procedura: specificare quali file vengono pubblicati da ClickOnce | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7ab6d724b40168f84227edb6ccfafc6245c30e0
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85381782"
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>Procedura: Specificare i file da pubblicare mediante ClickOnce
Quando si pubblica un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione, insieme all'applicazione vengono distribuiti tutti i file non di codice del progetto. In alcuni casi, è possibile che non si desideri o non sia necessario pubblicare determinati file o che si voglia installare determinati file in base alle condizioni. Visual Studio offre le funzionalità per escludere file, contrassegnare i file come file di dati o prerequisiti e creare gruppi di file per l'installazione condizionale.

 I file per un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione vengono gestiti nella finestra di dialogo **file applicazione** , accessibili dalla pagina **pubblica** di **Progettazione progetti**.

 Inizialmente, è presente un singolo gruppo di file denominato **(obbligatorio)**. È possibile creare altri gruppi di file e assegnarvi file. Non è possibile modificare il **gruppo di download** per i file necessari per l'esecuzione dell'applicazione. Il file con estensione exe o i file dell'applicazione contrassegnati come file di dati, ad esempio, devono appartenere al gruppo **(obbligatorio)** .

 Il valore predefinito per lo stato di pubblicazione di un file è contrassegnato con **(auto)**. Per impostazione predefinita, ad esempio, il file con estensione exe dell'applicazione ha lo stato di pubblicazione **include (auto)** .

 I file con la proprietà **azione di compilazione** impostata su **contenuto** sono designati come file dell'applicazione e verranno contrassegnati come inclusi per impostazione predefinita. Possono essere inclusi, esclusi o contrassegnati come file di dati. Le eccezioni sono le seguenti:

- Per impostazione predefinita, i file di dati quali i file di database SQL (con*estensione MDF* e *MDB*) e i file XML verranno contrassegnati come file di dati.

- I riferimenti agli assembly (file con*estensione dll* ) sono designati come indicato di seguito quando si aggiunge il riferimento: se **Copy Local** è **false**, è contrassegnato per impostazione predefinita come assembly prerequisiti (**prerequisito (auto)**) che deve essere presente nella GAC prima di installare l'applicazione. Se **Copy Local** è **true**, l'assembly è contrassegnato per impostazione predefinita come assembly dell'applicazione (**include (auto)**) e verrà copiato nella cartella dell'applicazione in fase di installazione. Un riferimento COM verrà visualizzato nella finestra di dialogo **file applicazione** (come file *ocx* ) solo se la relativa proprietà **isolata** è impostata su **true**. Per impostazione predefinita, verrà incluso.

### <a name="to-add-files-to-the-application-files-dialog-box"></a>Per aggiungere file alla finestra di dialogo file applicazione

1. Selezionare un file di dati in **Esplora soluzioni**.

2. Nella Finestra Proprietà impostare la proprietà **operazione di compilazione** sul valore del **contenuto** .

### <a name="to-exclude-files-from-clickonce-publishing"></a>Per escludere file dalla pubblicazione ClickOnce

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic sul pulsante **file applicazione** per aprire la finestra di dialogo **file applicazione** .

4. Nella finestra di dialogo **file applicazione** selezionare il file che si desidera escludere.

5. Nel campo **stato pubblicazione** selezionare **Escludi** dall'elenco a discesa.

### <a name="to-mark-files-as-data-files"></a>Per contrassegnare i file come file di dati

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic sul pulsante **file applicazione** per aprire la finestra di dialogo **file applicazione** .

4. Nella finestra di dialogo **file applicazione** selezionare il file che si desidera contrassegnare come dati.

5. Nel campo **stato pubblicazione** selezionare file di **dati** dall'elenco a discesa.

### <a name="to-mark-files-as-prerequisites"></a>Per contrassegnare i file come prerequisiti

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic sul pulsante **file applicazione** per aprire la finestra di dialogo **file applicazione** .

4. Nella finestra di dialogo **file applicazione** selezionare l'assembly dell'applicazione (file con*estensione dll* ) che si desidera contrassegnare come prerequisito. Si noti che l'applicazione deve avere un riferimento all'assembly dell'applicazione affinché venga visualizzata nell'elenco.

5. Nel campo **stato pubblicazione** selezionare **prerequisito** dall'elenco a discesa.

### <a name="to-add-a-new-file-group"></a>Per aggiungere un nuovo gruppo di file

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic sul pulsante **file applicazione** per aprire la finestra di dialogo **file applicazione** .

4. Nella finestra di dialogo **file applicazione** selezionare il campo **gruppo** per un file che si desidera includere nel nuovo gruppo.

    > [!NOTE]
    > Per i file è necessario che la proprietà **azione di compilazione** sia impostata su **contenuto** prima che i nomi file vengano visualizzati nella finestra di dialogo **file applicazione** .

5. Nel campo **Scarica gruppo** , selezionare **\<New...>** dall'elenco a discesa.

6. Nella finestra di dialogo **nuovo gruppo** immettere un nome per il gruppo e quindi fare clic su **OK**.

### <a name="to-add-a-file-to-a-group"></a>Per aggiungere un file a un gruppo

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic sul pulsante **file applicazione** per aprire la finestra di dialogo **file applicazione** .

4. Nella finestra di dialogo **file applicazione** selezionare il campo **gruppo** per un file che si desidera includere nel nuovo gruppo.

5. Nel campo **Scarica gruppo** selezionare un gruppo dall'elenco a discesa.

    > [!NOTE]
    > Non è possibile modificare il **gruppo di download** per i file necessari per l'esecuzione dell'applicazione.

## <a name="see-also"></a>Vedi anche
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)