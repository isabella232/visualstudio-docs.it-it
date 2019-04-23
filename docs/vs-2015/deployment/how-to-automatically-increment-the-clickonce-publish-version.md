---
title: 'Procedura: Incrementare il ClickOnce automaticamente versione pubblicazione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ab2dc62add13db9af1186a8974ffe5694a98e62e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60083503"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Procedura: Incrementare automaticamente il numero di versione pubblicazione dell'applicazione ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si pubblica un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione, la modifica di `Publish Version` fa sì che l'applicazione viene pubblicata come aggiornamento. Per impostazione predefinita, Visual Studio incrementa automaticamente il `Revision` numerose il `Publish Version` ogni volta che si pubblica l'applicazione.  
  
 È possibile disabilitare questo comportamento nel **Publish** pagina della **creazione progetti**.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>Per disabilitare a incremento automatico della versione di pubblicazione  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2. Fare clic sulla scheda **Pubblica**.  
  
3. Nel **Publish Version** sezione, deselezionare le **incrementa automaticamente revisione a ogni versione** casella di controllo.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Versione di pubblicazione di set di ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
