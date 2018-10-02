---
title: Proprietà delle proprietà di dominio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain properties
ms.assetid: a9471562-d6f2-46bf-9872-e0d66ba03150
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3c1bd47ce583c790fdc90a4135184b21a932f449
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526253"
---
# <a name="properties-of-domain-properties"></a>Proprietà delle proprietà di dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [delle proprietà di dominio proprietà](https://docs.microsoft.com/visualstudio/modeling/properties-of-domain-properties).  
  
Oggetto *proprietà del dominio* è una funzionalità di un elemento del modello che può contenere un valore. Ad esempio, la classe di dominio `Person` potrebbe includere le proprietà `Name` e `BirthDate`. Nella definizione DSL, le proprietà di dominio sono elencate nella casella della classe di dominio sul diagramma e sotto la classe di dominio in DSL Explorer. Per altre informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md).  
  
> [!NOTE]
>  Il termine"proprietà" ha due utilizzi. Oggetto *proprietà del dominio* è una funzionalità che si definisce una classe di dominio. Al contrario, dispongono di molti elementi di un linguaggio DSL *le proprietà*, in cui sono elencati il **proprietà** finestra nella definizione DSL. Ad esempio, ogni proprietà di dominio dispone di un set di proprietà descritte in questo argomento.  
  
 In fase di esecuzione, quando un utente crea un'istanza della classe di dominio, i valori delle proprietà di dominio sono visibili nella finestra Proprietà e possono essere visualizzati sulle forme.  
  
 La maggior parte delle proprietà di dominio è implementata come comuni proprietà CLR. Tuttavia, dal punto di vista della programmazione, le proprietà di dominio sono caratterizzate da funzionalità più avanzate rispetto alle proprietà del programma comuni.  
  
-   È possibile definire regole ed eventi per monitorare lo stato di una proprietà. Per altre informazioni, vedere [procedura: rispondere a e la propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md).  
  
-   Le transazioni contribuiscono a prevenire stati incoerenti. Per altre informazioni, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
 Quando si seleziona una Proprietà di dominio in un diagramma o in DSL Explorer, nella Finestra Proprietà vengono visualizzati gli elementi seguenti. Per altre informazioni su come usare questi elementi, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Proprietà|Descrizione|Valore predefinito|  
|--------------|-----------------|-------------------|  
|**Descrizione**|Descrizione usata per documentare l'interfaccia utente della finestra di progettazione generata.|\<Nessuno >|  
|**Nome visualizzato**|Nome che verrà visualizzato nella finestra di progettazione generata per questa proprietà di dominio. Può contenere spazi e punteggiatura, ad esempio "Song Title".|\<Nessuno >|  
|**Provider di nomi elemento**|Applicabile solo se `Is Element Name` è stato impostato su `true`. È possibile scrivere codice per assegnare un nome a un nuovo elemento in una classe di dominio, effettuando un override del comportamento predefinito.<br /><br /> In un file di codice nel progetto DSL, creare una classe derivata da <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider>.<br /><br /> In DSL Explorer fare quindi clic con il pulsante destro del mouse sulla radice del DSL e scegliere Aggiungi tipo esterno. Immettere il nome della classe.<br /><br /> Selezionare di nuovo questa proprietà di dominio e selezionare il nome della classe nell'elenco a discesa.|\<Nessuno >|  
|**Modificatore di accesso getter**|Livello di accesso della classe di dominio (`public` o `internal`). In tal modo viene controllato l'ambito nel quale il codice programma può accedere alla proprietà.|`public`|  
|**Parola chiave della Guida**|La parola chiave facoltativa usata per indicizzare la guida F1 per questa proprietà di dominio.|\<Nessuno >|  
|**È possibile visualizzare**|Se `True`, la proprietà di dominio è visualizzata dall'utente nella finestra delle proprietà quando i modelli di questo DSL sono aperti.<br /><br /> Se `False`, la proprietà di dominio è nascosta nell'interfaccia utente.<br /><br /> Se si desidera rendere la proprietà di dominio visibili ma in sola lettura, impostare **è dell'interfaccia utente di sola lettura**.|`True`|  
|**È nome elemento**|Se `True`, questa proprietà di dominio verrà visualizzata come nome del relativo elemento modello in DSL Explorer.<br /><br /> I nuovi elementi modello riceveranno un valore predefinito univoco per questa proprietà. Se si desidera controllare come vengono generati questi valori, impostare **Provider di nomi elemento**.|`False`|  
|**Interfaccia utente di sola lettura**|Se `True`, il valore della proprietà di dominio non può essere modificato tramite l'interfaccia utente. Può comunque essere impostato da programmi e sarà visibile nella finestra Proprietà.<br /><br /> Se si desidera nascondere le proprietà di dominio da parte dell'utente, impostare **è visualizzabile**. Se si desidera controllare l'accesso da parte di programmi, impostare **modificatore di accesso Setter**.|`False`|  
|**Kind**|Il tipo di proprietà di dominio (`Normal`, `Calculated` o `CustomStorage`). Per altre informazioni, vedere [calcolate e le proprietà di archiviazione personalizzate](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|  
|**Name**|Nome di questa proprietà di dominio. Deve essere un identificatore valido, ad esempio **SongTitle**.|\<Nessuno >|  
|**Note**|Note informali associate alla proprietà di dominio.|\<Nessuno >|  
|**Modificatore di accesso Setter**|Modificatore di accesso per il metodo Set. Consente di controllare l'ambito nel quale il codice programma può impostare la proprietà.|`public`|  
|**Type**|Tipo di proprietà. Per aggiungere all'elenco dei tipi disponibili, fare doppio clic la radice del DSL in DSL explorer e fare clic su **Aggiungi tipo esterno**.|`String`|  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario sugli strumenti Domain-Specific Language](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



