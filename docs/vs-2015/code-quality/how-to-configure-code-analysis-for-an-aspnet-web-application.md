---
title: "Procedura: configurare l'analisi del codice per un'applicazione Web ASP.NET | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 423264362118343d573b417cd055d2d722df995e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657457"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Procedura: configurare l'analisi del codice per un'applicazione Web ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] e [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] è possibile effettuare una selezione da un elenco di *set di regole* di analisi codice da applicare a [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] applicazione Web. Il set di regole predefinito è Microsoft Mininimum consigliate. È possibile selezionare un altro set di regole da applicare al sito Web.

### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>Per configurare un set di regole per un progetto del framework di pagine ASP.NET

1. Selezionare il sito Web in **Esplora soluzioni**.

2. Scegliere **Configura analisi codice per sito Web**dal menu **analizza** .

3. Se è stata selezionata la soluzione e la soluzione contiene più di un progetto, selezionare la configurazione della build e il sistema operativo di destinazione dagli elenchi **configurazione** e **piattaforma** .

4. Per ogni progetto nella soluzione, fare clic sulla colonna **set di regole** , quindi fare clic sul nome del set di regole da eseguire.

5. Per impostazione predefinita, l'analisi codice viene eseguita in tutti i progetti della soluzione. Per disabilitare o abilitare l'analisi del codice per un progetto specifico, attenersi alla procedura seguente:

    1. Fare clic con il pulsante destro del mouse sul nome del progetto, quindi scegliere Proprietà.

    2. Selezionare o deselezionare la casella di controllo **Abilita analisi codice** . È anche possibile eseguire manualmente l'analisi del codice selezionando **Esegui analisi codice sul sito Web** dal menu **analizza** .

6. Nell'elenco a discesa **Esegui questo set di regole** , attenersi alla seguente procedura:

    - Selezionare il set di regole che si desidera utilizzare.

    - Selezionare **\<Browse >** per specificare un set di regole personalizzato esistente non presente nell'elenco.

    - Definire un set di regole personalizzato. Per altre informazioni, vedere [creazione di set di regole personalizzati](../code-quality/creating-custom-code-analysis-rule-sets.md).
