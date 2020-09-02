---
title: "Procedura: impostare un'area di sicurezza per un'applicazione ClickOnce | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, security settings
- code access security, ClickOnce applications
- security zones, ClickOnce applications
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9af4507d7ccd604f82aae675bf87d36c0b039b26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68171423"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Procedura: impostare un'area di sicurezza per un'applicazione ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si impostano le autorizzazioni di sicurezza dall'accesso di codice per un'applicazione ClickOnce, è necessario iniziare con un set di autorizzazioni di base nella pagina **Sicurezza** di **Creazione progetti**.  
  
 Nella maggior parte dei casi è possibile anche scegliere l'area **Internet** che contiene un set di autorizzazioni limitato oppure l'area **Intranet locale** che contiene un set di autorizzazioni più esteso. Se l'applicazione richiede autorizzazioni personalizzate, è possibile scegliere l'area di sicurezza **Personalizzata** . Per altre informazioni sull'impostazione di autorizzazioni personalizzate, vedere [Procedura: Impostare le autorizzazioni personalizzate per un'applicazione ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
### <a name="to-set-a-security-zone"></a>Per impostare un'area di sicurezza  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **proprietà**dal menu **progetto** .  
  
2. Fare clic sulla scheda **Security** (Sicurezza).  
  
3. Selezionare la casella di controllo **Abilita impostazioni di sicurezza ClickOnce** .  
  
4. Selezionare il pulsante di opzione **È un'applicazione con attendibilità parziale** .  
  
     I controlli nella sezione **Autorizzazioni di sicurezza ClickOnce** sono abilitati.  
  
5. Dall'elenco a discesa **Area da cui verrà installata l'applicazione** selezionare un'area di sicurezza.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: impostare autorizzazioni personalizzate per un'applicazione ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Protezione delle applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)
