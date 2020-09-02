---
title: 'Procedura: abilitare le impostazioni di sicurezza ClickOnce | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d673edac957e9625f7d948fbe766ee08b23b6b52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382432"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Procedura: Abilitare le impostazioni di sicurezza ClickOnce
Per pubblicare l'applicazione, è necessario abilitare la sicurezza dall'accesso di codice per le applicazioni ClickOnce. Questa operazione viene eseguita automaticamente quando si pubblica un'applicazione tramite la pubblicazione guidata.

 In alcuni casi, l'abilitazione della sicurezza dall'accesso di codice può influisca sulle prestazioni durante la compilazione o il debug dell'applicazione. in questi casi, è possibile disabilitare temporaneamente le impostazioni di sicurezza.

 Le impostazioni di sicurezza ClickOnce possono essere abilitate o disabilitate nella pagina **sicurezza** di creazione **progetti**.

### <a name="to-enable-clickonce-security-settings"></a>Per abilitare le impostazioni di sicurezza ClickOnce

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Security** (Sicurezza).

3. Selezionare la casella di controllo **Abilita impostazioni di sicurezza ClickOnce** .

     È ora possibile personalizzare le impostazioni di sicurezza per l'applicazione nella pagina sicurezza.

    > [!NOTE]
    > Questa casella di controllo viene selezionata automaticamente ogni volta che l'applicazione viene pubblicata con la **pubblicazione** guidata.

### <a name="to-disable-clickonce-security-settings"></a>Per disabilitare le impostazioni di sicurezza ClickOnce

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Security** (Sicurezza).

3. Deselezionare la casella di controllo **Abilita impostazioni di sicurezza ClickOnce** .

     L'applicazione verrà eseguita con le impostazioni di sicurezza attendibilità totale; tutte le impostazioni nella pagina **sicurezza** verranno ignorate.

    > [!NOTE]
    > Ogni volta che l'applicazione viene pubblicata con la pubblicazione guidata, questa casella di controllo viene selezionata. è necessario cancellarlo di nuovo dopo ogni pubblicazione completata correttamente.

## <a name="see-also"></a>Vedere anche
- [Proteggere le applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)
- [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
