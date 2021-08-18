---
title: Sicurezza dall'accesso di codice per ClickOnce applicazioni | Microsoft Docs
description: Informazioni sulla sicurezza dall'accesso di codice per ClickOnce applicazioni e su come configurare le autorizzazioni di sicurezza dall'accesso di codice.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vb.XBAPProjectPropertiesSecurity.HowTo
- vb.XBAProjectPropertiesSecurity.HowTo
- vb.ProjectPropertiesSecurity.HowTo
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], security
- ClickOnce applications, caspol
- security [ClickOnce], WPF browser-hosted applications
- security [ClickOnce], ClickOnce applications
- ClickOnce applications, code access security policies
- security, ClickOnce
ms.assetid: 04b104d0-0bd3-4ccb-b164-1de92d234487
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 21d55ea85fe1075ef9c5bd8a7af238beaafc76e4ce6a142f9ecb16f639dd3cb1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121435686"
---
# <a name="code-access-security-for-clickonce-applications"></a>Sicurezza dall'accesso di codice per applicazioni ClickOnce
Le applicazioni ClickOnce sono basate sul Framework .NET e sono soggette a vincoli di sicurezza per l'accesso al codice. Per poter scrivere correttamente le applicazioni ClickOnce è quindi importante comprendere le implicazioni di questo tipo di sicurezza.

 La sicurezza dall’accesso di codice è un meccanismo di .NET Framework che consente di limitare l'accesso del codice alle risorse e alle operazioni protette. È necessario configurare le autorizzazioni per la sicurezza dell'accesso di codice per l'applicazione ClickOnce per usare l'area appropriata per la posizione del programma di installazione delle applicazioni. Nella maggior parte dei casi è possibile scegliere l'area **Internet** per un set di autorizzazioni limitato oppure l'area **Intranet locale** per un set di autorizzazioni più esteso.

## <a name="default-clickonce-code-access-security"></a>Sicurezza dell'accesso di codice ClickOnce predefinita
 Per impostazione predefinita, l'applicazione ClickOnce riceve autorizzazioni di attendibilità totale quando è installata o eseguita in un computer client.

- Un'applicazione con autorizzazioni di attendibilità totale ha un accesso illimitato alle risorse, ad esempio al file system e al registro. L'applicazione (e il sistema dell'utente finale) diventa però potenzialmente vulnerabile e potrebbe essere sfruttata da codice dannoso.

- Quando un'applicazione richiede autorizzazioni di attendibilità totale, è possibile che all'utente finale sia richiesto di concedere le autorizzazioni all'applicazione. Ciò significa che l'applicazione non fornisce effettivamente un'esperienza ClickOnce e, potenzialmente, la richiesta potrebbe confondere gli utenti meno esperti.

  > [!NOTE]
  > Quando si installa un'applicazione da un supporto rimovibile come un CD-ROM, non vengono inviate richieste all'utente. Inoltre, un amministratore di rete può configurare dei criteri di rete in modo che agli utenti non vengano inviate richieste quando installano un'applicazione da un'origine attendibile. Per altre informazioni, vedere [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md).

  Per limitare le autorizzazioni per un'applicazione ClickOnce, è possibile modificare le autorizzazioni per la sicurezza dell'accesso di codice per l'applicazione in modo da richiedere l'area più appropriata per le autorizzazioni necessarie all'applicazione. Nella maggior parte dei casi è possibile selezionare l'area da cui viene distribuita l'applicazione. Ad esempio, se l'applicazione è di tipo aziendale, è possibile usare l'area **Intranet locale** . Se l'applicazione è di tipo Internet, è possibile usare l'area **Internet** .

## <a name="configure-security-permissions"></a>Configurare le autorizzazioni di sicurezza
 È sempre necessario configurare l'applicazione ClickOnce per richiedere l'area appropriata per limitare le autorizzazioni per la sicurezza dell'accesso di codice. È possibile configurare le autorizzazioni di sicurezza nella pagina **Sicurezza** di **Creazione progetti**.

 La pagina **Sicurezza** in **Creazione progetti** contiene una casella di controllo **Abilita impostazioni di sicurezza ClickOnce** . Quando questa casella di controllo è selezionata, le richieste di autorizzazioni di sicurezza vengono aggiunte al manifesto della distribuzione per l'applicazione. Al momento dell'installazione all'utente verrà richiesto di concedere le autorizzazioni se le autorizzazioni richieste superano quelle predefinite per l'area da cui viene distribuita l'applicazione. Per altre informazioni, vedere [Procedura: Abilitare le ClickOnce di sicurezza.](../deployment/how-to-enable-clickonce-security-settings.md)

 Alle applicazioni distribuite da posizioni diverse vengono concessi livelli diversi di autorizzazioni senza richiesta di conferma. Ad esempio, se un'applicazione viene distribuita da Internet, riceve un set di autorizzazioni molto limitato. Se viene installata da una Intranet locale riceve un maggior numero di autorizzazioni, mentre se viene installata da CD-ROM riceve autorizzazioni di attendibilità totale.

 Come punto di partenza per la configurazione delle autorizzazioni, è possibile selezionare un'area di sicurezza dall'elenco **Area** nella pagina **Sicurezza** . Se l'applicazione potrebbe essere potenzialmente distribuita da più aree, selezionare l'area con il minor numero di autorizzazioni. Per altre informazioni, vedere [Procedura: Impostare un'area di sicurezza per un'applicazione ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md).

 Le proprietà che è possibile impostare variano in base al set di autorizzazioni. Non tutti i set di autorizzazioni dispongono di proprietà configurabili. Per altre informazioni sull'elenco completo di autorizzazioni che l'applicazione può richiedere, vedere <xref:System.Security.Permissions>. Per altre informazioni su come impostare le autorizzazioni per un'area personalizzata, vedere Procedura: Impostare autorizzazioni [personalizzate per un'ClickOnce app.](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)

## <a name="debug-an-application-that-has-restricted-permissions"></a>Eseguire il debug di un'applicazione con autorizzazioni limitate
 È probabile che uno sviluppatore usi le autorizzazioni di attendibilità totale nel computer di sviluppo. Quindi, quando esegue il debug dell'applicazione, non visualizzerà le stesse eccezioni di sicurezza visualizzate dagli utenti quando eseguono la stessa operazione con autorizzazioni limitate.

 Per rilevare queste eccezioni, è necessario eseguire il debug dell'applicazione con le stesse autorizzazioni dell'utente finale. Il debug con autorizzazioni limitate può essere abilitato nella pagina **Sicurezza** di **Creazione progetti**.

 Quando si esegue il debug di un'applicazione con autorizzazioni limitate, vengono generate eccezioni per ogni richiesta di sicurezza del codice non abilitata nella pagina **Sicurezza** . Viene visualizzato un supporto eccezioni che fornisce suggerimenti su come modificare il codice per evitare l'eccezione.

 Inoltre, quando si scrive codice, la funzionalità IntelliSense nell'editor del codice disabilita tutti i membri non inclusi nelle autorizzazioni di sicurezza configurate.

 Per altre informazioni, vedere [How to: Debug a ClickOnce Application with Restricted Permissions](securing-clickonce-applications.md).

## <a name="security-permissions-for-browser-hosted-applications"></a>Autorizzazioni di sicurezza per applicazioni ospitate da browser
 Visual Studio fornisce i seguenti tipi di progetto per le applicazioni Windows Presentation Foundation (WPF):

- Applicazione Windows WPF

- Applicazione Web Browser WPF

- Libreria di controlli personalizzati WPF

- Libreria di servizi WPF

  Di questi tipi di progetto, solo le applicazioni Web Browser WPF vengono ospitate in un Web browser e richiedono quindi impostazioni speciali di distribuzione e sicurezza. Le impostazioni di sicurezza predefinite per queste applicazioni sono le seguenti:

- **Abilitare ClickOnce sicurezza Impostazioni**

- **È un'applicazione parzialmente attendibile**

- **Area Internet** (con l'autorizzazione predefinita impostata per le applicazioni Web browser WPF selezionata)

  Nella finestra di dialogo **Impostazioni di sicurezza avanzate** la casella di controllo **Esegui debug dell'applicazione con il set di autorizzazioni selezionato** è selezionata e disabilitata. Il debug nell'area, infatti, non può essere disattivato per le applicazioni ospitate da browser.

## <a name="see-also"></a>Vedi anche
- [Proteggere le applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)
- [Procedura: Abilitare le impostazioni di sicurezza ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Procedura: Impostare un'area di sicurezza per un'applicazione ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Procedura: Impostare le autorizzazioni personalizzate per un'applicazione ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Procedura: Eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate](securing-clickonce-applications.md)
- [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md)
- [Pagina Sicurezza, Progettazione progetti](../ide/reference/security-page-project-designer.md)