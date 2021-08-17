---
title: Impostare autorizzazioni personalizzate (ClickOnce app)
description: Informazioni su come distribuire un'ClickOnce che usa le autorizzazioni predefinite o creare un'area personalizzata per le autorizzazioni specifiche necessarie per l'applicazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 240903c1f3335752986972131b17a27ed40bb3a4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073812"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Procedura: Impostare le autorizzazioni personalizzate per un'applicazione ClickOnce
È possibile distribuire un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] che usa le autorizzazioni predefinite per le aree Internet o Intranet locale. In alternativa, è possibile creare un'area personalizzata per le autorizzazioni specifiche necessarie all'applicazione. È possibile eseguire questa operazione personalizzando le autorizzazioni di sicurezza nella pagina **Sicurezza** di **Creazione progetti**.

### <a name="to-customize-a-permission"></a>Per personalizzare un'autorizzazione

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Security** (Sicurezza).

3. Selezionare la casella di controllo **Abilita impostazioni di sicurezza ClickOnce** .

4. Selezionare il pulsante di opzione **È un'applicazione con attendibilità parziale** .

     I controlli nella sezione **Autorizzazioni di sicurezza ClickOnce** sono abilitati.

5. Dall'elenco a discesa **Area da cui verrà installata l'applicazione** selezionare **(Personalizzata)**.

6. Fare clic su **Modifica XML autorizzazioni**.

     Il file *app.manifest* verrà aperto nell'editor XML.

7. Prima dell'elemento `</applicationRequestMinimum>` , aggiungere il codice XML per le autorizzazioni richieste dall'applicazione.

    > [!NOTE]
    > È possibile usare il metodo `ToXml` di un set di autorizzazioni per generare il codice XML per il manifesto dell'applicazione. Ad esempio, per generare il codice XML per il set di autorizzazioni <xref:System.Security.Permissions.EnvironmentPermission> , chiamare il metodo <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> .

## <a name="see-also"></a>Vedi anche
- [Proteggere ClickOnce applicazioni](../deployment/securing-clickonce-applications.md)
- [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
