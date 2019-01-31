---
title: 'Procedura: Impostare il ClickOnce versione pubblicazione | Microsoft Docs'
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7908bb88e13dff34721b7c6419d0a7f036be68d1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54923586"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Procedura: Impostare la versione pubblicazione per un'applicazione ClickOnce
Il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` proprietà determina se l'applicazione che si sta pubblicando verrà considerata un aggiornamento. Viene incrementato ogni versione di tempo, l'applicazione verrà pubblicata come aggiornamento.  
  
 Il `Publish Version` può impostare la proprietà il **Publish** pagina del **creazione progetti**.  
  
> [!NOTE]
>  È disponibile un'opzione di progetto che consente di incrementare automaticamente il `Publish Version` proprietà ogni volta che l'applicazione viene pubblicata; questa opzione è abilitata per impostazione predefinita. Per altre informazioni, vedere [Procedura: Incrementare automaticamente il numero di versione pubblicazione dell'applicazione ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### <a name="to-change-the-publish-version"></a>Per modificare la versione di pubblicazione  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic sulla scheda **Pubblica**.  
  
3.  In **Publish Version** campo, incrementare la **principali**, **secondaria**, **compilare**, o **revisione** versione numeri.  
  
    > [!NOTE]
    >  È non necessario diminuire mai un numero di versione; Questa operazione può provocare il comportamento di aggiornamento non prevedibili.  
  
## <a name="see-also"></a>Vedere anche  
 [Scegliere una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Procedura: Incrementare automaticamente il numero di versione pubblicazione dell'applicazione ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)