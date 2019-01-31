---
title: "Procedura: Modifica la lingua di pubblicazione di un'applicazione ClickOnce | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 67ac7693d4332c4dc5d6eae3fb89cf3e9a9c2384
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953030"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Procedura: Cambiare la lingua di pubblicazione di un'applicazione ClickOnce

Quando si pubblica un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione, l'interfaccia utente visualizzata durante l'installazione il valore predefinito è la lingua del computer di sviluppo. Se si pubblica un'applicazione localizzata, è necessario specificare una lingua e impostazioni cultura in base alla versione localizzata. Ciò è determinato dal `Publish language` proprietà per il progetto.

Il `Publish language` proprietà può essere impostata **Publish Options** finestra di dialogo, accessibile dal **pubblica** pagina della **Progettazione progetti**.

> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

## <a name="to-change-the-publish-language"></a>Per modificare la lingua di pubblicazione

1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2.  Fare clic sulla scheda **Pubblica**.

3.  Fare clic sui **le opzioni** pulsante per aprire il **Publish Options** nella finestra di dialogo.

4.  Fare clic su **descrizione**.

5.  Nel **Publish Options** finestra di dialogo selezionare una lingua e le impostazioni cultura dal **lingua di pubblicazione** elenco a discesa e quindi fare clic su **OK**.

## <a name="see-also"></a>Vedere anche

- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)