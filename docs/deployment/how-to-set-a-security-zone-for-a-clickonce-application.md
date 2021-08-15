---
title: Impostare l'area di sicurezza (ClickOnce app)
description: Informazioni sull'impostazione delle autorizzazioni di sicurezza dall'accesso di codice per un'applicazione ClickOnce, che inizia con un set di autorizzazioni di base in Project Designer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, security settings
- code access security, ClickOnce applications
- security zones, ClickOnce applications
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 88654d1d115ee84a13d541e26e085f1acf5c03e031900dcc6ab12e67efcf0c7e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403866"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Procedura: Impostare un'area di sicurezza per un'applicazione ClickOnce
Quando si impostano le autorizzazioni di sicurezza dall'accesso di codice per un'applicazione ClickOnce, è necessario iniziare con un set di autorizzazioni di base nella pagina **Sicurezza** di **Creazione progetti**.

 Nella maggior parte dei casi è possibile anche scegliere l'area **Internet** che contiene un set di autorizzazioni limitato oppure l'area **Intranet locale** che contiene un set di autorizzazioni più esteso. Se l'applicazione richiede autorizzazioni personalizzate, è possibile scegliere l'area di sicurezza **Personalizzata** . Per altre informazioni sull'impostazione di autorizzazioni personalizzate, vedere [Procedura: Impostare le autorizzazioni personalizzate per un'applicazione ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

### <a name="to-set-a-security-zone"></a>Per impostare un'area di sicurezza

1. Con un progetto selezionato in **Esplora soluzioni**, nel menu **Project** fare clic su **Proprietà**.

2. Fare clic sulla scheda **Security** (Sicurezza).

3. Selezionare la casella di controllo **Abilita impostazioni di sicurezza ClickOnce** .

4. Selezionare il pulsante di opzione **È un'applicazione con attendibilità parziale** .

     I controlli nella sezione **Autorizzazioni di sicurezza ClickOnce** sono abilitati.

5. Dall'elenco a discesa **Area da cui verrà installata l'applicazione** selezionare un'area di sicurezza.

## <a name="see-also"></a>Vedi anche
- [Procedura: Impostare le autorizzazioni personalizzate per un'applicazione ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Proteggere le applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)
- [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
