---
title: Avvisi di globalizzazione
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- warnings, globalization
- globalization warnings
- globalization [Visual Studio], warnings
- managed code analysis warnings, globalization warnings
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0815c17c85cb64682851f9b4af2b2f26f35109c5
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535858"
---
# <a name="globalization-warnings"></a>Avvisi di globalizzazione
Gli avvisi di globalizzazione supportano le librerie e le applicazioni predisposte per l'internazionalizzazione.

## <a name="in-this-section"></a>Contenuto della sezione

|Regola|Descrizione|
|----------|-----------------|
|[CA1300: Specificare MessageBoxOptions](../code-quality/ca1300.md)|Per visualizzare correttamente una finestra di messaggio per le impostazioni cultura che utilizzano un ordine di lettura da destra a sinistra, è necessario passare i membri RightAlign e RtlReading dell'enumerazione MessageBoxOptions al metodo Show.|
|[CA1301: Evitare tasti di scelta rapida duplicati](../code-quality/ca1301.md)|Un tasto di scelta o tasto di scelta rapida consente l'accesso da tastiera a un controllo mediante ALT. Quando più controlli hanno chiavi di accesso duplicate, il comportamento della chiave di accesso non è ben definito.|
|[CA1302: Non impostare come hardcoded le stringhe delle impostazioni locali](../code-quality/ca1302.md)|L'enumerazione System.Environment.SpecialFolder contiene membri che fanno riferimento a cartelle di sistema speciali. I percorsi di queste cartelle possono presentare valori diversi in sistemi operativi diversi. I percorso possono essere modificati e sono localizzati. Il metodo Environment. GetFolderPath restituisce i percorsi associati all'enumerazione Environment. SpecialFolder, localizzati e appropriati per il computer attualmente in esecuzione.|
|[CA1303: Non passare valori letterali come parametri localizzati](../code-quality/ca1303.md)|Un metodo visibile esternamente passa un valore letterale stringa come parametro a un metodo o un costruttore .NET e tale stringa deve essere localizzabile.|
|[CA1304: Specificare CultureInfo](../code-quality/ca1304.md)|Un metodo o un costruttore chiama un membro che presenta un overload che accetta un parametro System.Globalization.CultureInfo e tale metodo o costruttore non chiama l'overload che accetta il parametro CultureInfo. Quando non viene fornito un oggetto CultureInfo o System.IFormatProvider, il valore predefinito fornito dal membro di overload potrebbe non avere l'effetto desiderato in tutte le impostazioni locali.|
|[CA1305: Specificare IFormatProvider](../code-quality/ca1305.md)|Un metodo o un costruttore chiama uno o più membri con overload che accettano un parametro System.IFormatProvider e tale metodo o costruttore non chiama l'overload che accetta il parametro IFormatProvider. Quando non viene fornito un oggetto System.Globalization.CultureInfo o IFormatProvider, il valore predefinito fornito dal membro di overload potrebbe non avere l'effetto desiderato in tutte le impostazioni locali.|
|[CA1306: Specificare le impostazioni locali per i tipi di dati](../code-quality/ca1306.md)|Le impostazioni locali determinano elementi di presentazione specifici delle impostazioni cultura per i dati, ad esempio la formattazione utilizzata per valori numerici, simboli di valuta e criterio di ordinamento. Quando si crea un oggetto DataTable o DataSet, è opportuno definire in modo esplicito le impostazioni locali.|
|[CA1307: Specificare StringComparison](../code-quality/ca1307.md)|Un'operazione di confronto tra stringhe utilizza un overload del metodo che non imposta un parametro StringComparison.|
|[CA1308: Normalizzare le stringhe in lettere maiuscole](../code-quality/ca1308.md)|Le stringhe devono essere normalizzate in maiuscolo. Un piccolo gruppo di caratteri non è in grado di completare un round trip in caso di conversione in lettere minuscole.|
|[CA1309: Usare StringComparison ordinale](../code-quality/ca1309.md)|In un'operazione di confronto tra stringhe di tipo non linguistico il parametro StringComparison non viene impostato su Ordinal o OrdinalIgnoreCase. L'impostazione esplicita del parametro su StringComparison.Ordinal o StringComparison.OrdinalIgnoreCase consente spesso di rendere il codice più veloce, corretto e affidabile.|
|[CA2101: Specificare il marshalling per argomenti di stringa P/Invoke](../code-quality/ca2101.md)|Un membro platform invoke consente chiamanti parzialmente attendibili, presenta un parametro di stringa e non esegue il marshalling esplicito della stringa. Questo può comportare una potenziale vulnerabilità di sicurezza.|
