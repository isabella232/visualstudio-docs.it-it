---
title: Impostare la versione ClickOnce pubblicare | Microsoft Docs
description: Informazioni su come impostare la ClickOnce pubblica versione, che determina se l'applicazione è un aggiornamento.
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
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 39c126a1e2758bbbbc24c0f6ef5fa9b6310669eb
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627762"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Procedura: Impostare la versione pubblicazione per un'applicazione ClickOnce
La [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` proprietà determina se l'applicazione che si sta pubblicando verrà considerata o meno un aggiornamento. Ogni volta che la versione viene incrementata, l'applicazione verrà pubblicata come aggiornamento.

 La `Publish Version` proprietà può essere impostata nella pagina **Pubblica** di Progettazione **Project .**

> [!NOTE]
> È disponibile un'opzione di progetto che incrementa automaticamente la proprietà ogni volta che viene pubblicata l'applicazione. Questa `Publish Version` opzione è abilitata per impostazione predefinita. Per altre informazioni, vedere [Procedura: Incrementare automaticamente la versione ClickOnce pubblicazione.](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)

### <a name="to-change-the-publish-version"></a>Per modificare la versione di pubblicazione

1. Con un progetto selezionato in **Esplora soluzioni**, nel menu **Project** fare clic su **Proprietà**.

2. Fare clic sulla scheda **Pubblica**.

3. Nel **campo Versione** di pubblicazione incrementare i numeri di **versione** **principale,** **secondario,** build **o** revisione.

    > [!NOTE]
    > È consigliabile non decrementare mai un numero di versione. Questa operazione potrebbe causare un comportamento di aggiornamento imprevedibile.

## <a name="see-also"></a>Vedi anche
- [Scegliere una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Procedura: Incrementare automaticamente il numero di versione pubblicazione dell'applicazione ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: Pubblicare un'ClickOnce usando la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)