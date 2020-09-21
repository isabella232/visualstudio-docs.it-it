---
title: Incremento automatico della versione di pubblicazione ClickOnce
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6267e75db2e2a23d01368cdaa822d835cb8b844
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809794"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Procedura: Incrementare automaticamente il numero di versione della pubblicazione dell'applicazione ClickOnce

Quando si pubblica un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione, la modifica della `Publish Version` proprietà comporta la pubblicazione dell'applicazione come aggiornamento. Per impostazione predefinita, Visual Studio incrementa automaticamente il `Revision` numero di `Publish Version` ogni volta che si pubblica l'applicazione.

È possibile disabilitare questo comportamento nella pagina **pubblica** di **Progettazione progetti**.

> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>Per disabilitare automaticamente l'incremento della versione di pubblicazione

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Nella sezione **Pubblica versione** deselezionare la casella di controllo **incrementa automaticamente revisione a ogni versione** .

## <a name="see-also"></a>Vedere anche

- [Procedura: Impostare la versione pubblicazione per un'applicazione ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)