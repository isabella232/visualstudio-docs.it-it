---
title: 'CA1824: contrassegnare gli assembly con NeutralResourcesLanguageAttribute | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 19077a63d5aa22bda3f968943703a82488e2745d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545288"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Contrassegnare gli assembly con NeutralResourcesLanguageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Category|Microsoft. performance|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un assembly contiene una risorsa basata su **resx** <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> a cui non è applicato l'oggetto.

## <a name="rule-description"></a>Descrizione della regola
 L'attributo **NeutralResourcesLanguage** informa l'oggetto **ResourceManager** del linguaggio usato per visualizzare le risorse delle impostazioni cultura non associate ad alcun paese per un assembly. Quando cerca le risorse nelle stesse impostazioni cultura della lingua delle risorse neutre, **ResourceManager** usa automaticamente le risorse che si trovano nell'assembly principale. Esegue questa operazione anziché cercare un assembly satellite con le impostazioni cultura dell'interfaccia utente correnti per il thread corrente. Tale approccio migliora le prestazioni delle ricerche per la prima risorsa caricata e riduce il working set.

## <a name="fixing-violations"></a>Correzione di violazioni
 Per correggere una violazione di questa regola, aggiungere l'attributo all'assembly e specificare la lingua delle risorse delle impostazioni cultura non associate ad alcun paese.

## <a name="specifying-the-language"></a>Specifica della lingua

#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Per specificare la lingua della risorsa delle impostazioni cultura non associate ad alcun paese

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **Proprietà**.

2. Nella barra di spostamento a sinistra selezionare **applicazione**, quindi fare clic su **informazioni assembly**.

3. Nella finestra di dialogo **informazioni assembly** selezionare la lingua dall'elenco a discesa **lingua neutra** .

4. Fare clic su **OK**.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola. Tuttavia, le prestazioni di avvio potrebbero ridursi.
