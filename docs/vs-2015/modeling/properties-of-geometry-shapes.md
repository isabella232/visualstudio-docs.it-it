---
title: Proprietà delle forme geometriche | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords:
- Domain-Specific Language, geometry shape
ms.assetid: 3993a23e-eab3-4ceb-b475-c395d5992bfc
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 70424ef2b3ce091b1c1290db2c4962481c9f68ca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540489"
---
# <a name="properties-of-geometry-shapes"></a>Proprietà delle forme geometriche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [delle proprietà di forme geometriche](https://docs.microsoft.com/visualstudio/modeling/properties-of-geometry-shapes).  
  
Per specificare come vengono visualizzate le istanze delle classi di dominio in un linguaggio specifico di dominio, è possibile usare forme geometriche. Per altre informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md). Per altre informazioni su come usare queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Forme geometriche hanno le proprietà elencate nella tabella seguente.  
  
|Proprietà|Descrizione|Impostazione predefinita|  
|--------------|-----------------|-------------|  
|Colore riempimento|Il colore di riempimento di questa forma.|Bianco|  
|Modalità di sfumatura riempimento|La modalità di sfumatura riempimento della forma (orizzontale, verticale, diagonali in avanti, con le versioni precedenti diagonale o None).|Orizzontale|  
|Geometry|La geometria della forma (rettangolo, rettangolo con angoli arrotondati, dell'ellisse o cerchio).|Rettangolo|  
|Offre punti di connessione predefinito|Se `True`, la forma userà superiore, inferiore, sinistro e i punti di connessione a destra nella finestra di progettazione generata.|False|  
|Colore del contorno|Colore del contorno di questa forma.|Nero|  
|Stile del tratteggio di struttura|Lo stile di tratteggio contorno di questa forma (tinta unita, Dash, Dot, Trattopunto, Trattopuntopunto o personalizzato).|Tinta unita|  
|Spessore del contorno|Lo spessore del contorno di questa forma.|0.03125|  
|Colore del testo|Colore utilizzato per gli elementi Decorator di testo associati a questa forma.|Nero|  
|Modificatore di accesso|Il modificatore di accesso della classe (pubblico o interno).|Public|  
|Attributi personalizzati|Consente di aggiungere attributi alla classe di codice sorgente generato per questa forma.|\<Nessuno >|  
|Genera l'errore doppia derivati|Se `True`, verrà generate una classe di base sia una classe parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Ha un costruttore personalizzato|Se `True`, verrà fornito un costruttore personalizzato nel codice sorgente. Per altre informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generato dalla forma (`none`, `abstract` o `sealed`).|none|  
|Forma geometria di base|Classe di base di questa forma.|(nessuno)|  
|nome|Il nome di questa forma.|Nome corrente|  
|Spazio dei nomi|Lo spazio dei nomi che è affiliato a questa forma.|Spazio dei nomi corrente|  
|Tipo della descrizione comando|Modalità la descrizione comando viene definito (fisso, variabile o none). Se viene risolto, quindi il valore della `Fixed Tooltip Text` proprietà viene usata come descrizione comando; se la variabile, la descrizione comando è definito nel codice personalizzato.|nessuno|  
|Note|Note informali associate a questo elemento.|\<Nessuno >|  
|Altezza iniziale|Altezza iniziale della forma, in pollici.|1|  
|Larghezza iniziale|Larghezza iniziale della forma, in pollici.|1,5|  
|Colore di riempimento esposte come proprietà<br /><br /> Modalità di sfumatura riempimento esposto<br /><br /> Esposizione del colore del contorno come proprietà<br /><br /> Esposta dello stile di tratteggio di struttura come proprietà<br /><br /> Esposti come proprietà dello spessore del contorno<br /><br /> Espone il colore del testo|Se `True`, l'utente può impostare la proprietà specificata di una forma. Per procedere, fare doppio clic la definizione della forma e fare clic su **Aggiungi esposta**.|False|  
|Descrizione|La descrizione che consente di documentare la finestra di progettazione generata.|\<Nessuno >|  
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generata per questa forma.|\<Nessuno >|  
|Testo della descrizione comando fissa|Testo che viene usato per una descrizione comando fissa.|\<Nessuno >|  
|Parola chiave della Guida|La parola chiave utilizzata per indicizzare la Guida F1 per questa forma.|\<Nessuno >|  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario sugli strumenti Domain-Specific Language](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



