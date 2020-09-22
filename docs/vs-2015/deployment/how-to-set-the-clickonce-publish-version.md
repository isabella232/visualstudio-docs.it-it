---
title: 'Procedura: impostare la versione di pubblicazione ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ec5d5d742b5a0749d1d5d52cee0a0545dd8570f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839600"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Procedura: impostare la versione pubblicazione per un'applicazione ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `Publish Version` proprietà determina se l'applicazione che si sta pubblicando verrà considerata come un aggiornamento. Ogni volta che viene incrementata la versione, l'applicazione verrà pubblicata come aggiornamento.  
  
 La `Publish Version` proprietà può essere impostata nella pagina **pubblica** di **Progettazione progetti**.  
  
> [!NOTE]
> È disponibile un'opzione di progetto che incrementerà automaticamente la `Publish Version` Proprietà ogni volta che viene pubblicata l'applicazione. questa opzione è abilitata per impostazione predefinita. Per ulteriori informazioni, vedere [procedura: incrementare automaticamente la versione di pubblicazione ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### <a name="to-change-the-publish-version"></a>Per modificare la versione di pubblicazione  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **proprietà**dal menu **progetto** .  
  
2. Fare clic sulla scheda **Pubblica**.  
  
3. Nel **campo versione di pubblicazione** , incrementare i numeri di versione **principale**, **secondario**, **Build**o **Revisione** .  
  
    > [!NOTE]
    > Non decrementare mai un numero di versione; Questa operazione potrebbe causare un comportamento di aggiornamento imprevedibile.  
  
## <a name="see-also"></a>Vedere anche  
 [Scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Procedura: incrementare automaticamente la versione di pubblicazione ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
