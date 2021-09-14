---
title: Pagina Sicurezza, Progettazione progetti
description: La pagina Sicurezza di Creazione progetti consente di configurare le impostazioni di sicurezza dall'accesso di codice per le applicazioni distribuite usando la distribuzione ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 426179eb20fcb71ac02039c3b2be20dab6f685b3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627132"
---
# <a name="security-page-project-designer"></a>Pagina Sicurezza, Progettazione progetti

La pagina **Sicurezza** di **Creazione progetti** consente di configurare le impostazioni di sicurezza dall'accesso di codice per le applicazioni distribuite usando la distribuzione ClickOnce. Per altre informazioni, vedere [Sicurezza dall'accesso di codice per ClickOnce applicazioni](../../deployment/code-access-security-for-clickonce-applications.md).

Per accedere alla pagina **Sicurezza**, fare clic su un nodo di progetto in **Esplora soluzioni** e quindi scegliere **Proprietà** dal menu **Progetto**. Quando viene visualizzata la finestra **Creazione progetti** fare clic sulla scheda **Sicurezza**.

## <a name="security-settings"></a>Impostazioni di sicurezza

 **Abilitare ClickOnce sicurezza Impostazioni**

Determina se le impostazioni di sicurezza sono abilitate in fase di progettazione. Se questa opzione è deselezionata, tutte le altre opzioni della pagina **Sicurezza** non sono disponibili.

> [!NOTE]
> Quando si pubblica un'applicazione usando la procedura guidata di **pubblicazione** questa opzione è abilitata automaticamente.

Quando si seleziona questa opzione, è possibile selezionare uno dei due pulsanti di opzione disponibili: **È un'applicazione con attendibilità totale** o **È un'applicazione con attendibilità parziale**.

Per impostazione predefinita, l'opzione è selezionata per i progetti Applicazione Web browser WPF.

Per impostazione predefinita, per tutti gli altri tipi di progetto l'opzione è deselezionata.

 **È un'applicazione con attendibilità totale**

Se si seleziona questa opzione, l'applicazione richiede le autorizzazioni Attendibilità totale quando è installata o eseguita in un computer client. Evitare l'uso dell'attendibilità totale, se possibile, perché all'applicazione verrà concesso l'accesso illimitato a risorse come il file system e il registro.

Per impostazione predefinita, l'opzione è impostata su Attendibilità parziale per i progetti Applicazione Web browser WPF.

Per impostazione predefinita, per tutti gli altri tipi di progetto l'opzione è impostata su Attendibilità totale.

 **È un'applicazione parzialmente attendibile**

Se si seleziona questa opzione, l'applicazione richiede le autorizzazioni Attendibilità parziale quando è installata o eseguita in un computer client. *Attendibilità parziale* significa che verranno eseguite solo le azioni consentite dalle autorizzazioni di sicurezza dall'accesso di codice richieste. Per altre informazioni sulla configurazione delle autorizzazioni di sicurezza, vedere [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

È possibile specificare le impostazioni di sicurezza con attendibilità parziale configurando le opzioni dell'area **Autorizzazioni di sicurezza ClickOnce**.

## <a name="clickonce-security-permissions"></a>Autorizzazioni di sicurezza ClickOnce

 **Zona da cui verrà installata l'applicazione**

Specifica un set predefinito di autorizzazioni di sicurezza dall'accesso di codice. Scegliere **Internet** o **Intranet locale** per un set di autorizzazioni oppure **(Personalizzato)** per configurare un set di autorizzazioni personalizzato. Se l'applicazione richiede più autorizzazioni rispetto a quelle concesse in una zona, viene visualizzata una richiesta di attendibilità ClickOnce per l'utente finale per la concessione delle autorizzazioni aggiuntive. Per altre informazioni sulla configurazione delle autorizzazioni di sicurezza, vedere [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

Per impostazione predefinita, l'opzione è impostata su **Internet** per i progetti Applicazione Web browser WPF.

 **Modifica XML autorizzazioni**

Apre il modello di manifesto dell'applicazione (app.manifest) per configurare le autorizzazioni per il set di autorizzazioni **(Personalizzato)**.

 **Funzionalità avanzate**

Apre la [finestra di dialogo Impostazioni di sicurezza avanzate](../../ide/reference/advanced-security-settings-dialog-box.md), che consente di configurare le impostazioni per il debug dell'applicazione con autorizzazioni con restrizioni. Queste impostazioni vengono controllate durante il debug e le eccezioni delle autorizzazioni indicano che l'applicazione può richiedere più autorizzazioni oltre a quelle definite in una zona.

## <a name="see-also"></a>Vedi anche

- <xref:System.Security.Permissions.WebBrowserPermission>
- <xref:System.Security.Permissions.MediaPermission>
- [Sicurezza dall'accesso di codice per ClickOnce applicazioni](../../deployment/code-access-security-for-clickonce-applications.md)
- [Procedura: Abilitare ClickOnce sicurezza Impostazioni](../../deployment/how-to-enable-clickonce-security-settings.md)
- [Procedura: Impostare un'area di sicurezza per un ClickOnce app ClickOnce sicurezza](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Procedura: Impostare autorizzazioni personalizzate per un'ClickOnce personalizzata](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Proteggere ClickOnce app](../../deployment/securing-clickonce-applications.md)
- [ClickOnce Sicurezza e distribuzione](../../deployment/clickonce-security-and-deployment.md)
- [Project Properties Reference](../../ide/reference/project-properties-reference.md) (Riferimenti alle proprietà di progetto)
- [Finestra di dialogo Impostazioni di sicurezza avanzate](../../ide/reference/advanced-security-settings-dialog-box.md)
