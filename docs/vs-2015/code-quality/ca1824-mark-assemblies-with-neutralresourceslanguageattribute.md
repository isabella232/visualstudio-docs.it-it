---
title: 'CA1824: Contrassegnare gli assembly con NeutralResourcesLanguageAttribute | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: 13f635398ecab7c0bd9436a86a43a15d4908b163
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892597"
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



