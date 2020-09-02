---
title: "Procedura: abilitare l'avvio automatico per le installazioni di CD | Microsoft Docs"
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153781"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Procedura: attivare l'avvio automatico per le installazioni da CD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si distribuisce un' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione per mezzo di supporti rimovibili, ad esempio CD-ROM o DVD-ROM, è possibile abilitare in `AutoStart` modo che l' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione venga avviata automaticamente al momento dell'inserimento del supporto.  
  
 `AutoStart` può essere abilitato nella pagina **pubblica** di **Progettazione progetti**.  
  
### <a name="to-enable-autostart"></a>Per abilitare l'avvio automatico  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **proprietà**dal menu **progetto** .  
  
2. Fare clic sulla scheda **Pubblica**.  
  
3. Fare clic sul pulsante **Opzioni** .  
  
     Verrà visualizzata la finestra di dialogo **Opzioni di pubblicazione** .  
  
4. Fare clic su **Distribuzione**.  
  
5. Selezionare la casella **di controllo per le installazioni CD, avvia automaticamente il programma di installazione quando viene inserito CD** .  
  
     Un file Autorun. inf verrà copiato nel percorso di pubblicazione quando viene pubblicata l'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
