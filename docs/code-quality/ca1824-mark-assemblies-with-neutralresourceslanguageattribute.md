---
title: 'CA1824: Contrassegnare gli assembly con NeutralResourcesLanguageAttribute'
ms.date: 03/29/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db780257c83c42f97500a83f1843332cae0ecea3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825176"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Contrassegnare gli assembly con NeutralResourcesLanguageAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Un assembly contiene un **ResX**-risorsa basata su ma non dispone di <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> applicato.

## <a name="rule-description"></a>Descrizione della regola

Il <xref:System.Resources.NeutralResourcesLanguageAttribute> attributi informa il gestore di risorse delle impostazioni cultura predefinite dell'app. Se l'impostazione predefinita le risorse di lingua sono incorporate nell'assembly principale dell'app, e <xref:System.Resources.ResourceManager> è recuperare le risorse che appartengono alle stesse impostazioni cultura le impostazioni cultura predefinite, il <xref:System.Resources.ResourceManager> usa automaticamente le risorse che si trovano nell'assembly principale invece di cercare un assembly satellite. Ciò consente di ignorare il probe di assembly normale, migliora le prestazioni della ricerca per la prima risorsa caricata e riduce il working set.

> [!TIP]
> Visualizzare [creazione di pacchetti e distribuzione delle risorse](/dotnet/framework/resources/packaging-and-deploying-resources-in-desktop-apps) per il processo che <xref:System.Resources.ResourceManager> Usa per verificare la presenza di file di risorse.

## <a name="fix-violations"></a>Correggere le violazioni

Per correggere una violazione di questa regola, aggiungere l'attributo all'assembly e specificare la lingua delle risorse delle impostazioni cultura neutre.

### <a name="to-specify-the-neutral-language-for-resources"></a>Per specificare la lingua neutra per le risorse

1. Nelle **Esplora soluzioni**mouse sul progetto e quindi selezionare **proprietà**.

2. Selezionare il **Application** scheda e quindi selezionare **informazioni sugli Assembly**.

   > [!NOTE]
   > Se il progetto è un progetto .NET Core o .NET Standard, selezionare la **pacchetto** scheda.

3. Selezionare la lingua dal **lingua neutra** oppure **lingua neutra Assembly** elenco a discesa.

4. Scegliere **OK**.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola. Tuttavia, potrebbero compromettere le prestazioni di avvio.

## <a name="see-also"></a>Vedere anche

- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- [Risorse nelle App desktop (.NET)](/dotnet/framework/resources/)
- [CA1703: le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1701: stringa di risorsa parole composte devono essere digitate correttamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)