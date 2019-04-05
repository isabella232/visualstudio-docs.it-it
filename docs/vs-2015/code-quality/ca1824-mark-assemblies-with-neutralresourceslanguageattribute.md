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
ms.openlocfilehash: 8690a1f05f54fbac9427f4a03412e0a8054c51d2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966959"
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

1.  Nelle **Esplora soluzioni**mouse sul progetto e quindi fare clic su **proprietà**.

2.  Dalla barra di spostamento a sinistra selezionare **Application**, quindi fare clic su **informazioni sugli Assembly**.

3.  Nel **informazioni sull'Assembly** finestra di dialogo, selezionare la lingua dal **lingua neutra** elenco a discesa.

4.  Fare clic su **OK**.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola. Tuttavia, potrebbero ridurre le prestazioni di avvio.
