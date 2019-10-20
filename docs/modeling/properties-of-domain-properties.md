---
title: Proprietà delle proprietà di dominio
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain properties
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: debf263fa18d2a6af8e95ee959002686540e2c06
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658196"
---
# <a name="properties-of-domain-properties"></a>Proprietà delle proprietà di dominio
Una *proprietà di dominio* è una funzionalità di un elemento del modello che può ospitare un valore. Ad esempio, la classe di dominio `Person` potrebbe includere le proprietà `Name` e `BirthDate`. Nella definizione DSL, le proprietà di dominio sono elencate nella casella della classe di dominio sul diagramma e sotto la classe di dominio in DSL Explorer. Per ulteriori informazioni, vedere [come definire un Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md).

> [!NOTE]
> Il termine"proprietà" ha due utilizzi. Una *proprietà di dominio* è una funzionalità definita in una classe di dominio. Al contrario, molti elementi di un linguaggio DSL hanno *Proprietà*, elencate nella finestra **Proprietà** nella definizione DSL. Ad esempio, ogni proprietà di dominio dispone di un set di proprietà descritte in questo argomento.

 In fase di esecuzione, quando un utente crea un'istanza della classe di dominio, i valori delle proprietà di dominio sono visibili nella finestra Proprietà e possono essere visualizzati sulle forme.

 La maggior parte delle proprietà di dominio è implementata come comuni proprietà CLR. Tuttavia, dal punto di vista della programmazione, le proprietà di dominio sono caratterizzate da funzionalità più avanzate rispetto alle proprietà del programma comuni.

- È possibile definire regole ed eventi per monitorare lo stato di una proprietà. Per ulteriori informazioni, vedere [risposta a e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md).

- Le transazioni contribuiscono a prevenire stati incoerenti. Per ulteriori informazioni, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).

  Quando si seleziona una Proprietà di dominio in un diagramma o in DSL Explorer, nella Finestra Proprietà vengono visualizzati gli elementi seguenti. Per ulteriori informazioni sull'utilizzo di questi elementi, vedere [personalizzazione ed estensione di un Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

|proprietà|Descrizione|Valore predefinito|
|-|-|-|
|**Descrizione**|Descrizione usata per documentare l'interfaccia utente della finestra di progettazione generata.|\<nessuno>|
|**Nome visualizzato**|Nome che verrà visualizzato nella finestra di progettazione generata per questa proprietà di dominio. Può contenere spazi e punteggiatura, ad esempio "Song Title".|\<nessuno>|
|**Provider nome elemento**|Applicabile solo se `Is Element Name` è stato impostato su `true`. È possibile scrivere codice per assegnare un nome a un nuovo elemento in una classe di dominio, effettuando un override del comportamento predefinito.<br /><br /> In un file di codice nel progetto DSL, creare una classe derivata da <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider>.<br /><br /> In DSL Explorer fare quindi clic con il pulsante destro del mouse sulla radice del DSL e scegliere Aggiungi tipo esterno. Immettere il nome della classe.<br /><br /> Selezionare di nuovo questa proprietà di dominio e selezionare il nome della classe nell'elenco a discesa.|\<nessuno>|
|**Modificatore di accesso Getter**|Livello di accesso della classe di dominio (`public` o `internal`). In tal modo viene controllato l'ambito nel quale il codice programma può accedere alla proprietà.|`public`|
|**Parola chiave della Guida**|La parola chiave facoltativa usata per indicizzare la guida F1 per questa proprietà di dominio.|\<nessuno>|
|**È esplorabile**|Se `True`, la proprietà di dominio è visualizzata dall'utente nella finestra delle proprietà quando i modelli di questo DSL sono aperti.<br /><br /> Se `False`, la proprietà di dominio è nascosta nell'interfaccia utente.<br /><br /> Se si desidera rendere visibile la proprietà del dominio ma in sola lettura, impostare **è interfaccia utente**di sola lettura.|`True`|
|**Nome elemento**|Se `True`, questa proprietà di dominio verrà visualizzata come nome del relativo elemento modello in DSL Explorer.<br /><br /> I nuovi elementi modello riceveranno un valore predefinito univoco per questa proprietà. Se si desidera controllare la modalità di generazione di questi valori, impostare **provider nome elemento**.|`False`|
|**Interfaccia utente di sola lettura**|Se `True`, il valore della proprietà di dominio non può essere modificato tramite l'interfaccia utente. Può comunque essere impostato da programmi e sarà visibile nella finestra Proprietà.<br /><br /> Se si desidera nascondere la proprietà del dominio dall'utente, set **è esplorabile**. Se si vuole controllare l'accesso tramite programmi, impostare il **modificatore di accesso Setter**.|`False`|
|**Tipo**|Il tipo di proprietà di dominio (`Normal`, `Calculated` o `CustomStorage`). Per altre informazioni, vedere [proprietà di archiviazione calcolate e personalizzate](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|
|**Nome**|Nome di questa proprietà di dominio. Deve essere un identificatore valido, ad esempio **SongTitle**.|\<nessuno>|
|**Note**|Note informali associate alla proprietà di dominio.|\<nessuno>|
|**Modificatore di accesso Setter**|Modificatore di accesso per il metodo Set. Consente di controllare l'ambito nel quale il codice programma può impostare la proprietà.|`public`|
|**Type**|Tipo di proprietà. Per aggiungere l'elenco dei tipi disponibili, fare clic con il pulsante destro del mouse sulla radice del DSL in DSL Explorer e scegliere **Aggiungi tipo esterno**.|`String`|

## <a name="see-also"></a>Vedere anche

- [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)