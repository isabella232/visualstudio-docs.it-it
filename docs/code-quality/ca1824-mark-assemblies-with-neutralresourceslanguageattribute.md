---
title: 'CA1824: Contrassegnare gli assembly con NeutralResourcesLanguageAttribute'
ms.date: 03/29/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df5c0db4e9e141e5833893bbbb447328eab8851e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233349"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Contrassegnare gli assembly con NeutralResourcesLanguageAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Category|Microsoft.Performance|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un assembly contiene una risorsa basata su **resx**a cui non è applicato <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> l'oggetto.

## <a name="rule-description"></a>Descrizione della regola

L' <xref:System.Resources.NeutralResourcesLanguageAttribute> attributo informa Resource Manager delle impostazioni cultura predefinite di un'app. Se le risorse delle impostazioni cultura predefinite sono incorporate nell'assembly principale dell'app e <xref:System.Resources.ResourceManager> devono recuperare le risorse che appartengono alle stesse impostazioni cultura predefinite <xref:System.Resources.ResourceManager> , USA automaticamente le risorse presenti nell'assembly principale. anziché cercare un assembly satellite. Questo ignora il consueto Probe assembly, migliora le prestazioni di ricerca per la prima risorsa caricata e può ridurre il working set.

> [!TIP]
> Vedere Creazione del [pacchetto e distribuzione delle risorse](/dotnet/framework/resources/packaging-and-deploying-resources-in-desktop-apps) per <xref:System.Resources.ResourceManager> il processo usato da per verificare la presenza di file di risorse.

## <a name="fix-violations"></a>Correggi violazioni

Per correggere una violazione di questa regola, aggiungere l'attributo all'assembly e specificare la lingua delle risorse delle impostazioni cultura non associate ad alcun paese.

### <a name="to-specify-the-neutral-language-for-resources"></a>Per specificare la lingua neutra per le risorse

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **Proprietà**.

2. Selezionare la scheda **applicazione** , quindi selezionare **informazioni assembly**.

   > [!NOTE]
   > Se il progetto è un progetto .NET Standard o .NET Core, selezionare la scheda **pacchetto** .

3. Selezionare la lingua nell'elenco a discesa lingua **neutra** o **lingua indipendente dall'assembly** .

4. Scegliere **OK**.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola. Tuttavia, le prestazioni di avvio potrebbero peggiorare.

## <a name="see-also"></a>Vedere anche

- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- [Risorse nelle applicazioni desktop (.NET)](/dotnet/framework/resources/)
- [CA1703: le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1701: le parole composte di stringhe di risorse devono essere configurate correttamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)