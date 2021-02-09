---
title: Impostare la versione di pubblicazione ClickOnce | Microsoft Docs
description: Informazioni su come impostare la proprietà della versione di pubblicazione ClickOnce, che determina se l'applicazione è un aggiornamento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 71d74d8b16e058b150187a231a1f3a7323c0c612
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885027"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Procedura: Impostare la versione pubblicazione per un'applicazione ClickOnce
La [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` proprietà determina se l'applicazione che si sta pubblicando verrà considerata come un aggiornamento. Ogni volta che viene incrementata la versione, l'applicazione verrà pubblicata come aggiornamento.

 La `Publish Version` proprietà può essere impostata nella pagina **pubblica** di **Progettazione progetti**.

> [!NOTE]
> È disponibile un'opzione di progetto che incrementerà automaticamente la `Publish Version` Proprietà ogni volta che viene pubblicata l'applicazione. questa opzione è abilitata per impostazione predefinita. Per ulteriori informazioni, vedere [procedura: incrementare automaticamente la versione di pubblicazione ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).

### <a name="to-change-the-publish-version"></a>Per modificare la versione di pubblicazione

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **proprietà** dal menu **progetto** .

2. Fare clic sulla scheda **Pubblica**.

3. Nel **campo versione di pubblicazione** , incrementare i numeri di versione **principale**, **secondario**, **Build** o **Revisione** .

    > [!NOTE]
    > Non decrementare mai un numero di versione; Questa operazione potrebbe causare un comportamento di aggiornamento imprevedibile.

## <a name="see-also"></a>Vedi anche
- [Scegliere una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Procedura: Incrementare automaticamente il numero di versione pubblicazione dell'applicazione ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)