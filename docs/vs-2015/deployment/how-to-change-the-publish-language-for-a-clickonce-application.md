---
title: "Procedura: modifica la lingua di pubblicazione di un'applicazione ClickOnce | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: 2330f234b5b00fdde99376fbe5664bd5dbd99551
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49239657"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Procedura: cambiare la lingua di pubblicazione di un'applicazione ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si pubblica un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione, l'interfaccia utente visualizzata durante l'installazione il valore predefinito è la lingua del computer di sviluppo. Se si pubblica un'applicazione localizzata, è necessario specificare una lingua e impostazioni cultura in base alla versione localizzata. Ciò è determinato dal `Publish language` proprietà per il progetto.  
  
 Il `Publish language` proprietà può essere impostata **Publish Options** finestra di dialogo, accessibile dal **pubblica** pagina della **Progettazione progetti**.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-change-the-publish-language"></a>Per modificare la lingua di pubblicazione  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Scegliere il **pubblica** scheda.  
  
3.  Fare clic sui **le opzioni** pulsante per aprire il **Publish Options** nella finestra di dialogo.  
  
4.  Fare clic su **descrizione**.  
  
5.  Nel **Publish Options** finestra di dialogo selezionare una lingua e le impostazioni cultura dal **lingua di pubblicazione** elenco a discesa e quindi fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



