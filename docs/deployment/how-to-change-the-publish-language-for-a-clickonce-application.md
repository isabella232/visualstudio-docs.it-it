---
title: Modificare la lingua di pubblicazione per l'applicazione ClickOnce
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0252cf39f8f5ee268adbf625f03a9b5a305b903a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382588"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Procedura: Cambiare la lingua di pubblicazione di un'applicazione ClickOnce

Quando si pubblica un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione, l'interfaccia utente visualizzata durante l'installazione viene impostata in modo predefinito sulla lingua e le impostazioni cultura del computer di sviluppo. Se si pubblica un'applicazione localizzata, sarà necessario specificare una lingua e le impostazioni cultura corrispondenti alla versione localizzata. Questa operazione è determinata dalla `Publish language` proprietà per il progetto.

La `Publish language` proprietà può essere impostata nella finestra di dialogo **Opzioni di pubblicazione** accessibile dalla pagina **pubblica** di **Progettazione progetti**.

> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

## <a name="to-change-the-publish-language"></a>Per modificare la lingua di pubblicazione

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic sul pulsante **Opzioni** per aprire la finestra di dialogo **Opzioni di pubblicazione** .

4. Fare clic su **Descrizione**.

5. Nella finestra di dialogo **Opzioni di pubblicazione** selezionare una lingua e le impostazioni cultura dall'elenco a discesa **lingua di pubblicazione** , quindi fare clic su **OK**.

## <a name="see-also"></a>Vedere anche

- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)