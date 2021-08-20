---
title: Modificare la lingua di pubblicazione per ClickOnce appalta
description: Informazioni su come specificare una lingua/impostazioni cultura per un'applicazione di localizzazione in ClickOnce, anziché usare per impostazione predefinita la lingua o le impostazioni cultura del computer di sviluppo.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 4e34b5a28df05758eb24d6af2c907e99d0f9b9f7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160829"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Procedura: Cambiare la lingua di pubblicazione di un'applicazione ClickOnce

Quando si pubblica un'applicazione, l'interfaccia utente visualizzata durante l'installazione viene utilizzata per impostazione predefinita per la lingua e [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le impostazioni cultura del computer di sviluppo. Se si pubblica un'applicazione localizzata, è necessario specificare una lingua e le impostazioni cultura corrispondenti alla versione localizzata. Ciò è determinato dalla `Publish language` proprietà per il progetto.

La proprietà può essere impostata nella finestra di dialogo Opzioni di pubblicazione , accessibile dalla `Publish language` **pagina Pubblica** di progettazione **Project .** 

> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

## <a name="to-change-the-publish-language"></a>Per modificare la lingua di pubblicazione

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic **sul pulsante** Opzioni per aprire la finestra di **dialogo Opzioni** di pubblicazione .

4. Fare clic **su Descrizione**.

5. Nella finestra **di dialogo Opzioni** di pubblicazione  selezionare una lingua e impostazioni cultura dall'elenco a discesa Lingua di pubblicazione e quindi fare clic su **OK.**

## <a name="see-also"></a>Vedi anche

- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: Pubblicare un'ClickOnce usando la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)