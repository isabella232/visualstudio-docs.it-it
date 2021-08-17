---
title: Abilitare ClickOnce sicurezza Impostazioni | Microsoft Docs
description: Informazioni su come la pubblicazione guidata abilita automaticamente la sicurezza dall'accesso di codice ClickOnce applicazioni per pubblicare l'applicazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: b534d18deeb63cad6cb0df967915e4fde968c688
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080624"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Procedura: Abilitare le impostazioni di sicurezza ClickOnce
La sicurezza dall'accesso di ClickOnce deve essere abilitata per pubblicare l'applicazione. Questa operazione viene eseguita automaticamente quando si pubblica un'applicazione tramite la pubblicazione guidata.

 In alcuni casi, l'abilitazione della sicurezza dall'accesso di codice può influire sulle prestazioni durante la compilazione o il debug dell'applicazione. In questi casi, è possibile disabilitare temporaneamente le impostazioni di sicurezza.

 ClickOnce le impostazioni di sicurezza possono essere  abilitate o disabilitate nella pagina Sicurezza di **Project Designer**.

### <a name="to-enable-clickonce-security-settings"></a>Per abilitare le ClickOnce di sicurezza

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Security** (Sicurezza).

3. Selezionare la casella di controllo **Abilita impostazioni di sicurezza ClickOnce** .

     È ora possibile personalizzare le impostazioni di sicurezza per l'applicazione nella pagina Sicurezza.

    > [!NOTE]
    > Questa casella di controllo viene selezionata automaticamente ogni volta che l'applicazione viene pubblicata con la **Pubblicazione** guidata.

### <a name="to-disable-clickonce-security-settings"></a>Per disabilitare ClickOnce di sicurezza

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Security** (Sicurezza).

3. Deselezionare **la casella ClickOnce sicurezza Impostazioni.**

     L'applicazione verrà eseguita con le impostazioni di sicurezza con attendibilità totale. Tutte le impostazioni nella **pagina** Sicurezza verranno ignorate.

    > [!NOTE]
    > Ogni volta che l'applicazione viene pubblicata con la Pubblicazione guidata, questa casella di controllo verrà selezionata. è necessario cancellarlo di nuovo dopo ogni pubblicazione completata.

## <a name="see-also"></a>Vedi anche
- [Proteggere le applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)
- [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
