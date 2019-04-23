---
title: 'CA1824: Contrassegnare gli assembly con NeutralResourcesLanguageAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 795d48b96392057a3f96cf3a67f3c49de8aee9b9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052168"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Contrassegnare gli assembly con NeutralResourcesLanguageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un assembly contiene un **ResX**-risorsa basata su ma non dispone di <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> applicato.

## <a name="rule-description"></a>Descrizione della regola
 Il **NeutralResourcesLanguage** attributo indica il **ResourceManager** del linguaggio che è stato usato per visualizzare le risorse delle impostazioni cultura di sistema per un assembly. Quando esegue la ricerca di risorse con le stesse impostazioni cultura per la lingua risorse neutra, le **ResourceManager** usa automaticamente le risorse che si trovano nell'assembly principale. Ciò avviene invece di cercare un assembly satellite con le impostazioni cultura dell'interfaccia utente corrente per il thread corrente. Tale approccio migliora le prestazioni delle ricerche per la prima risorsa caricata e riduce il working set.

## <a name="fixing-violations"></a>Correzione delle violazioni
 Per correggere una violazione di questa regola, aggiungere l'attributo all'assembly e specificare la lingua delle risorse delle impostazioni cultura neutre.

## <a name="specifying-the-language"></a>Che specifica il linguaggio

#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Per specificare la lingua della risorsa delle impostazioni cultura neutre

1. Nelle **Esplora soluzioni**mouse sul progetto e quindi fare clic su **proprietà**.

2. Dalla barra di spostamento a sinistra selezionare **Application**, quindi fare clic su **informazioni sugli Assembly**.

3. Nel **informazioni sull'Assembly** finestra di dialogo, selezionare la lingua dal **lingua neutra** elenco a discesa.

4. Fare clic su **OK**.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola. Tuttavia, potrebbero ridurre le prestazioni di avvio.
