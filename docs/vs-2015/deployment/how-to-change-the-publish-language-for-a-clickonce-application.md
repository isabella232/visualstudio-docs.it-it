---
title: "Procedura: modifica della lingua di pubblicazione per un'applicazione ClickOnce | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 26e4074b731dad44cd9eed40f1c1cc755d786562
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683805"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Procedura: cambiare la lingua di pubblicazione di un'applicazione ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si pubblica un' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione, l'interfaccia utente visualizzata durante l'installazione viene impostata in modo predefinito sulla lingua e le impostazioni cultura del computer di sviluppo. Se si pubblica un'applicazione localizzata, sarà necessario specificare una lingua e le impostazioni cultura corrispondenti alla versione localizzata. Questa operazione è determinata dalla `Publish language` proprietà per il progetto.  
  
 La `Publish language` proprietà può essere impostata nella finestra di dialogo **Opzioni di pubblicazione** accessibile dalla pagina **pubblica** di **Progettazione progetti**.  
  
> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-change-the-publish-language"></a>Per modificare la lingua di pubblicazione  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2. Fare clic sulla scheda **Pubblica**.  
  
3. Fare clic sul pulsante **Opzioni** per aprire la finestra di dialogo **Opzioni di pubblicazione** .  
  
4. Fare clic su **Descrizione**.  
  
5. Nella finestra di dialogo **Opzioni di pubblicazione** selezionare una lingua e le impostazioni cultura dall'elenco a discesa **lingua di pubblicazione** , quindi fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
