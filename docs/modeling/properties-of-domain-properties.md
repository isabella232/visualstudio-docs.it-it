---
title: Proprietà delle proprietà di dominio
description: Informazioni su come una proprietà di dominio è una funzionalità di un elemento del modello che può contenere un valore e come le proprietà di dominio sono elencate nella casella della classe di dominio nel diagramma.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 0d2305e63c33e7a8fa5b3a4c7bad68f1ee4fe70039a380384712a73c69b74221
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121428887"
---
# <a name="properties-of-domain-properties"></a>Proprietà delle proprietà di dominio
Una *proprietà di dominio* è una funzionalità di un elemento del modello che può contenere un valore. Ad esempio, la classe di dominio `Person` potrebbe includere le proprietà `Name` e `BirthDate`. Nella definizione DSL, le proprietà di dominio sono elencate nella casella della classe di dominio sul diagramma e sotto la classe di dominio in DSL Explorer. Per altre informazioni, vedere [How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md).

> [!NOTE]
> Il termine"proprietà" ha due utilizzi. Una *proprietà di dominio* è una funzionalità definita in una classe di dominio. Al contrario, molti elementi di un DSL hanno proprietà *,* elencate nella **finestra** Proprietà nella definizione DSL. Ad esempio, ogni proprietà di dominio dispone di un set di proprietà descritte in questo argomento.

 In fase di esecuzione, quando un utente crea un'istanza della classe di dominio, i valori delle proprietà di dominio sono visibili nella finestra Proprietà e possono essere visualizzati sulle forme.

 La maggior parte delle proprietà di dominio è implementata come comuni proprietà CLR. Tuttavia, dal punto di vista della programmazione, le proprietà di dominio sono caratterizzate da funzionalità più avanzate rispetto alle proprietà del programma comuni.

- È possibile definire regole ed eventi per monitorare lo stato di una proprietà. Per altre informazioni, vedere [Risposta e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md).

- Le transazioni contribuiscono a prevenire stati incoerenti. Per altre informazioni, vedere [Esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).

  Quando si seleziona una Proprietà di dominio in un diagramma o in DSL Explorer, nella Finestra Proprietà vengono visualizzati gli elementi seguenti. Per altre informazioni su come usare questi elementi, vedere Personalizzazione ed estensione di [un Domain-Specific linguaggio](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Proprietà|Descrizione|Valore predefinito|
|-|-|-|
|**Descrizione**|Descrizione usata per documentare l'interfaccia utente della finestra di progettazione generata.|\<none>|
|**Nome visualizzato**|Nome che verrà visualizzato nella finestra di progettazione generata per questa proprietà di dominio. Può contenere spazi e punteggiatura, ad esempio "Song Title".|\<none>|
|**Provider del nome di elemento**|Applicabile solo se `Is Element Name` è stato impostato su `true`. È possibile scrivere codice per assegnare un nome a un nuovo elemento in una classe di dominio, effettuando un override del comportamento predefinito.<br /><br /> In un file di codice nel progetto DSL, creare una classe derivata da <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider>.<br /><br /> In DSL Explorer fare quindi clic con il pulsante destro del mouse sulla radice del DSL e scegliere Aggiungi tipo esterno. Immettere il nome della classe.<br /><br /> Selezionare di nuovo questa proprietà di dominio e selezionare il nome della classe nell'elenco a discesa.|\<none>|
|**Modificatore di accesso con metodo Get**|Livello di accesso della classe di dominio (`public` o `internal`). In tal modo viene controllato l'ambito nel quale il codice programma può accedere alla proprietà.|`public`|
|**Parola chiave della Guida**|La parola chiave facoltativa usata per indicizzare la guida F1 per questa proprietà di dominio.|\<none>|
|**È visualizzabile**|Se `True`, la proprietà di dominio è visualizzata dall'utente nella finestra delle proprietà quando i modelli di questo DSL sono aperti.<br /><br /> Se `False`, la proprietà di dominio è nascosta nell'interfaccia utente.<br /><br /> Se si vuole rendere visibile la proprietà di dominio ma di sola lettura, impostare **È di sola lettura dell'interfaccia utente.**|`True`|
|**È Nome elemento**|Se `True`, questa proprietà di dominio verrà visualizzata come nome del relativo elemento modello in DSL Explorer.<br /><br /> I nuovi elementi modello riceveranno un valore predefinito univoco per questa proprietà. Per controllare la modalità di generazione di questi valori, impostare **Provider nome elemento**.|`False`|
|**È di sola lettura nell'interfaccia utente**|Se `True`, il valore della proprietà di dominio non può essere modificato tramite l'interfaccia utente. Può comunque essere impostato da programmi e sarà visibile nella finestra Proprietà.<br /><br /> Se si vuole nascondere la proprietà di dominio all'utente, impostare **Is Browsable**. Per controllare l'accesso da parte dei programmi, impostare **Modificatore di accesso setter**.|`False`|
|**Tipologia**|Il tipo di proprietà di dominio (`Normal`, `Calculated` o `CustomStorage`). Per altre informazioni, vedere [Calculated and Custom Archiviazione Properties](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|
|**Nome**|Nome di questa proprietà di dominio. Deve essere un identificatore valido, ad esempio **SongTitle**.|\<none>|
|**Note**|Note informali associate alla proprietà di dominio.|\<none>|
|**Modificatore di accesso con metodo Set**|Modificatore di accesso per il metodo Set. Consente di controllare l'ambito nel quale il codice programma può impostare la proprietà.|`public`|
|**Tipo**|Tipo di proprietà. Per aggiungere all'elenco dei tipi disponibili, fare clic con il pulsante destro del mouse sulla radice del DSL in Esplora DSL e scegliere **Aggiungi tipo esterno**.|`String`|

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))