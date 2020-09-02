---
title: 'Procedura: incrementare automaticamente la versione di pubblicazione ClickOnce | Microsoft Docs'
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
ms.openlocfilehash: 50faf70e8eda6ef7ab01201102540729497eb87b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683914"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Procedura: incrementare automaticamente il numero di versione pubblicazione dell'applicazione ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si pubblica un' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione, la modifica della `Publish Version` proprietà comporta la pubblicazione dell'applicazione come aggiornamento. Per impostazione predefinita, Visual Studio incrementa automaticamente il `Revision` numero di `Publish Version` ogni volta che si pubblica l'applicazione.  
  
 È possibile disabilitare questo comportamento nella pagina **pubblica** di **Progettazione progetti**.  
  
> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>Per disabilitare automaticamente l'incremento della versione di pubblicazione  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2. Fare clic sulla scheda **Pubblica**.  
  
3. Nella sezione **Pubblica versione** deselezionare la casella di controllo **incrementa automaticamente revisione a ogni versione** .  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: impostare la versione di pubblicazione ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
