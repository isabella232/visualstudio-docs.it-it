---
title: Regole di globalizzazione
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- rules, globalization
- globalization rules
- globalization [Visual Studio], rules
- managed code analysis rules, globalization rules
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e046f7e885ea0a6002d07b6a06b6b3728bf607aa
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808639"
---
# <a name="globalization-rules"></a>Regole di globalizzazione
Le regole di globalizzazione supportano le librerie e le applicazioni predisposte per l'internazionalizzazione.

## <a name="in-this-section"></a>Contenuto della sezione

|Regola|Descrizione|
|----------|-----------------|
|[CA1303: Non passare valori letterali come parametri localizzati](../code-quality/ca1303.md)|Un metodo visibile esternamente passa un valore letterale stringa come parametro a un metodo o un costruttore .NET e tale stringa deve essere localizzabile.|
|[CA1304: Specificare CultureInfo](../code-quality/ca1304.md)|Un metodo o un costruttore chiama un membro che presenta un overload che accetta un parametro System.Globalization.CultureInfo e tale metodo o costruttore non chiama l'overload che accetta il parametro CultureInfo. Quando non viene fornito un oggetto CultureInfo o System.IFormatProvider, il valore predefinito fornito dal membro di overload potrebbe non avere l'effetto desiderato in tutte le impostazioni locali.|
|[CA1305: Specificare IFormatProvider](../code-quality/ca1305.md)|Un metodo o un costruttore chiama uno o più membri con overload che accettano un parametro System.IFormatProvider e tale metodo o costruttore non chiama l'overload che accetta il parametro IFormatProvider. Quando non viene fornito un oggetto System.Globalization.CultureInfo o IFormatProvider, il valore predefinito fornito dal membro di overload potrebbe non avere l'effetto desiderato in tutte le impostazioni locali.|
|[CA1306: Specificare le impostazioni locali per i tipi di dati](../code-quality/ca1306.md)|Le impostazioni locali determinano elementi di presentazione specifici delle impostazioni cultura per i dati, ad esempio la formattazione utilizzata per valori numerici, simboli di valuta e criterio di ordinamento. Quando si crea un oggetto DataTable o DataSet, è opportuno definire in modo esplicito le impostazioni locali.|
|[CA1307: Specificare StringComparison per la chiarezza](../code-quality/ca1307.md)|Un'operazione di confronto tra stringhe utilizza un overload del metodo che non imposta un parametro StringComparison.|
|[CA1308: Normalizzare le stringhe in lettere maiuscole](../code-quality/ca1308.md)|Le stringhe devono essere normalizzate in maiuscolo. Un piccolo gruppo di caratteri non è in grado di completare un round trip in caso di conversione in lettere minuscole.|
|[CA1309: Usare StringComparison ordinale](../code-quality/ca1309.md)|In un'operazione di confronto tra stringhe di tipo non linguistico il parametro StringComparison non viene impostato su Ordinal o OrdinalIgnoreCase. L'impostazione esplicita del parametro su StringComparison.Ordinal o StringComparison.OrdinalIgnoreCase consente spesso di rendere il codice più veloce, corretto e affidabile.|
|[CA1310: Specificare StringComparison per la correttezza](../code-quality/ca1310.md)|Un'operazione di confronto tra stringhe usa un overload del metodo che non imposta un parametro StringComparison e usa il confronto di stringhe specifico delle impostazioni cultura per impostazione predefinita.|
|[CA2101: specificare il marshalling per gli argomenti di stringa P/Invoke](../code-quality/ca2101.md)|Un membro platform invoke consente chiamanti parzialmente attendibili, presenta un parametro di stringa e non esegue il marshalling esplicito della stringa. Questo può comportare una potenziale vulnerabilità di sicurezza.|
