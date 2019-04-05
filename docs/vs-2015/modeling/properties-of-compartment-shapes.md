---
title: Proprietà delle forme di raggruppamento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
ms.assetid: 9a9e112d-210d-413b-a44f-0e976a4a78bc
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 69fac0b8ef5c17a8d66d32730e189f2813aa1158
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955531"
---
# <a name="properties-of-compartment-shapes"></a>Proprietà delle forme di raggruppamento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Forme raggruppamento sono una delle forme che è possibile usare per la visualizzazione di una classe di dominio in un linguaggio specifico di dominio. È possibile espandere e comprimere i raggruppamenti.  
  
 Per altre informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md). Per altre informazioni su come usare queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Forme raggruppamento hanno le proprietà elencate nella tabella seguente.  
  
|Proprietà|Descrizione|Impostazione predefinita|  
|--------------|-----------------|-------------|  
|Predefinito espandere lo stato di compressione|Se `Expanded`, i raggruppamenti sono mostrati al momento della creazione. Se `Collapsed`, non lo siano.|Espanso|  
|Colore riempimento|Il colore di riempimento di questa forma.|Bianco|  
|Modalità di sfumatura riempimento|La modalità di sfumatura riempimento della forma.|Orizzontale|  
|Geometry|La geometria della forma (rettangolo o un rettangolo arrotondato).|Rettangolo|  
|Offre punti di connessione predefinito|Se `True`, la forma userà superiore, inferiore, sinistro e i punti di connessione a destra nella finestra di progettazione generata.|False|  
|È visibile l'intestazione del singolo raggruppamento|Se `False`e la forma presenta un singolo raggruppamento, l'intestazione del raggruppamento non è visibile.|True|  
|Colore del contorno|Colore del contorno di questa forma.|Nero|  
|Stile del tratteggio di struttura|Lo stile di tratteggio contorno di questa forma (tinta unita, trattino, punto, Trattopunto, Trattopuntopunto, personalizzato).|Tinta unita|  
|Spessore del contorno|Lo spessore del contorno di questa forma.|0.03125|  
|Colore del testo|Colore utilizzato per gli elementi Decorator di testo associati a questa forma.|Nero|  
|Modificatore di accesso|Il livello di accesso della forma di raggruppamento (`public` o `internal`).|Public|  
|Attributi personalizzati|Consente di aggiungere attributi alla classe di codice sorgente generato da questa forma di raggruppamento|\<nessuno>|  
|Genera l'errore doppia derivati|Se `True`, verrà generate una classe di base sia una classe parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Ha un costruttore personalizzato|Se `True`, verrà fornito un costruttore personalizzato nel codice sorgente. Per altre informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generato dalla forma di raggruppamento (`none`, `abstract` o `sealed`).|nessuno|  
|Forma raggruppamento di base|Classe di base di questa forma.|(nessuno)|  
|Nome|Il nome di questa forma.|Nome corrente|  
|Spazio dei nomi|Lo spazio dei nomi che è affiliato a questa forma.|Spazio dei nomi corrente|  
|Tipo della descrizione comando|Modalità la descrizione comando viene definito (fisso, variabile o none). Se viene risolto, quindi il valore della `Fixed Tooltip Text` proprietà viene usata come descrizione comando; se la variabile, la descrizione comando è definito nel codice personalizzato.|none|  
|Note|Note informali associate a questa forma.|\<nessuno>|  
|Altezza iniziale|Altezza iniziale della forma, in pollici. Per le forme di raggruppamento, questo è l'altezza della sezione dell'intestazione solo e che non può essere ridimensionata.|1|  
|Larghezza iniziale|Larghezza iniziale di questa forma, in pollici.|1,5|  
|Colore di riempimento esposte come proprietà<br /><br /> Modalità di sfumatura riempimento esposto<br /><br /> Esposizione del colore del contorno come proprietà<br /><br /> Esposta dello stile di tratteggio di struttura come proprietà<br /><br /> Esposti come proprietà dello spessore del contorno<br /><br /> Espone il colore del testo|Se `True`, l'utente può impostare la proprietà specificata di una forma. Per procedere, fare doppio clic la definizione della forma e fare clic su **Aggiungi esposta**.|False|  
|Descrizione|Consente di documentare la finestra di progettazione generata.|\<nessuno>|  
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generata per questa forma.|\<nessuno>|  
|Testo della descrizione comando fissa|Testo che viene usato per una descrizione comando fissa.|\<nessuno>|  
|Parola chiave della Guida|La parola chiave utilizzata per indicizzare la Guida F1 per questa forma.|\<nessuno>|  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario di Strumenti Domain-Specific Language](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
