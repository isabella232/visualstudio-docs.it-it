---
title: Configurare l'analisi del codice per l'app Web ASP.NET
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 1483ba4ea8e726ed61dc7c65ec486d420dbeb8a2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021936"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Procedura: Configurare l'analisi codice per un'applicazione Web ASP.NET

In Visual Studio, è possibile selezionare da un elenco di analisi del codice *set di regole* da applicare a [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] applicazione web. Il set di regole predefinito è regole minime consigliate di Microsoft. È possibile selezionare un'altra regola da applicare al sito web.

1. Selezionare il sito web in **Esplora soluzioni**.

2. Nel **Analyze** menu, fare clic su **Configura analisi codice per sito Web**.

3. Se è stata selezionata la soluzione e la soluzione contiene più di un progetto, selezionare il sistema operativo di configurazione e di destinazione compilazione dal **Configuration** e **piattaforma** Elenca.

4. Per ogni progetto nella soluzione, scegliere il **del Set di regole** colonna e quindi scegliere il nome della regola impostata per l'esecuzione.

5. Per impostazione predefinita, l'analisi del codice viene eseguito su tutti i progetti nella soluzione. Per disabilitare o abilitare l'analisi codice per un particolare progetto, seguire questa procedura:

    1. Il pulsante destro del mouse e quindi fare clic su proprietà.

    2. Selezionare o deselezionare i **Attiva analisi codice** casella di controllo. È anche possibile eseguire manualmente l'analisi del codice selezionando **Esegui analisi del codice sul sito Web** dalle **Analizza** menu.

6. Nel **eseguire questo set di regole** elenco a discesa elenco, seguire questa procedura:

    - Selezionare il set di regole che si desidera utilizzare.

    - Selezionare  **\<Sfoglia >** per specificare set di una regola personalizzata esistente non incluso nell'elenco.

    - Definire un [set di regole personalizzate](../code-quality/how-to-create-a-custom-rule-set.md).