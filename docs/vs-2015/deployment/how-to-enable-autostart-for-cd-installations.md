---
title: "Procedura: Attivare l'avvio automatico per le installazioni da CD | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c4bd14060517793d28e24818a051df63efb8f0e0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061100"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Procedura: Attivare l'avvio automatico per le installazioni da CD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si distribuisce un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione mediante supporti rimovibili, ad esempio CD-ROM o DVD-ROM di avvio, è possibile abilitare `AutoStart` in modo che il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione viene avviata automaticamente dopo l'inserimento del supporto.  
  
 `AutoStart` può essere abilitata per il **Publish** pagina della **creazione progetti**.  
  
### <a name="to-enable-autostart"></a>Abilitare l'avvio automatico  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2. Fare clic sulla scheda **Pubblica**.  
  
3. Fare clic sul pulsante **Opzioni**.  
  
     Il **Publish Options** verrà visualizzata la finestra di dialogo.  
  
4. Fare clic su **distribuzione**.  
  
5. Selezionare il **per installazioni da CD, avvia automaticamente l'installazione all'inserimento del CD** casella di controllo.  
  
     Un file Autorun verrà copiato nel percorso di pubblicazione è pubblicata l'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
