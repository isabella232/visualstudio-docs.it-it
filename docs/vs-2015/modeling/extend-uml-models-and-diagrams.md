---
title: Estendere modelli e diagrammi UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: b5bfa61e-ea59-4c3b-b5af-53475d7d13cd
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 917c88056709cfbeb89ce3f19d9c8da9866feb4e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68182865"
---
# <a name="extend-uml-models-and-diagrams"></a>Estendere modelli e diagrammi UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo argomento sono riepilogati i diversi modi in cui è possibile estendere gli strumenti di modellazione UML di Visual Studio. Per individuare le versioni di Visual Studio che supportano i singoli tipi di modello e strumenti, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
 Nello scenario di esempio seguente Fabrikam progetta e installa sistemi di gestione bagagli in aeroporto. I progetti di diversi aeroporti presentano molte analogie in termini di attrezzatura di base e software che la controlla. Vi sono però anche molti fattori che variano notevolmente, come la configurazione dei nastri trasportatori, i banchi del check-in, i contenitori di stoccaggio e altre apparecchiature per la gestione dei bagagli.  
  
 All'inizio di un nuovo progetto, il team di Fabrikam crea un modello UML per discutere dei requisiti internamente e con il cliente. Vengono usati i diagrammi di attività per rappresentare il flusso dei bagagli, con nodi oggetto che rappresentano le singole attrezzature. Il modello UML non rappresenta direttamente il codice del sistema.  
  
 Il team degli strumenti di Fabrikam appronta una serie di miglioramenti per i team di sviluppo. Nelle sezioni seguenti sono descritti i tipi diversi di estensione che è possibile definire. È possibile combinare tra loro molte di queste tecniche in un'unica estensione di Visual Studio.  
  
 Per altre informazioni, vedere questo video: ![collegamento a video](../data-tools/media/playvideo.gif "PlayVideo")[MSDN How Do I Series: Strumenti ed estendibilità ULM](http://go.microsoft.com/fwlink/?LinkId=214467).  
  
## <a name="Requirements"></a> Requisiti  
  
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
- [SDK di modellazione per Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=48148).  
  
## <a name="profiles"></a>Profili  
 I profili consentono di definire gli stereotipi e le proprietà aggiuntive negli elementi UML.  
  
 Gli sviluppatori di strumenti di Fabrikam definiscono gli stereotipi nei nodi oggetto dei diagrammi di attività, ad esempio "nastro trasportatore" e "banco check-in". Quando un membro del team crea uno schema per la gestione bagagli usando un diagramma di attività, può impostare gli stereotipi per indicare il tipo di attrezzatura rappresentato da ciascun nodo. Gli sviluppatori di strumenti definiscono le proprietà aggiuntive in alcuni stereotipi, in modo da consentire agli utenti di registrare valori come la capacità di un nastro trasportatore e il lato operativo del banco check-in.  
  
 Per altre informazioni, vedere [definire un profilo per estendere UML](../modeling/define-a-profile-to-extend-uml.md).  
  
## <a name="custom-toolbox-items"></a>Elementi della casella degli strumenti personalizzati  
 Un elemento della casella degli strumenti personalizzata crea un elemento o un gruppo di elementi da un prototipo definito in un diagramma. È possibile ad esempio creare uno strumento che consente di creare casi di utilizzo in un determinato colore o stereotipo oppure un gruppo di classi e associazioni che rappresenta uno schema progettuale. È possibile aggiungere questi elementi della casella degli strumenti nelle estensioni di Visual Studio e distribuirli ad altri utenti.  
  
 Per altre informazioni, vedere [definire un oggetto personalizzato elemento della casella degli strumenti di modellazione](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
## <a name="validation"></a>Convalida  
 È possibile definire regole per assicurarsi che un modello UML sia conforme ai vincoli specificati.  
  
 Gli sviluppatori di strumenti di Fabrikam definiscono regole per evitare ai membri del team di commettere semplici errori nei modelli di gestione dei bagagli. Ad esempio, un banco del check-in non può essere connesso direttamente al contenitore di stoccaggio, ma tra essi deve esserci almeno un nastro trasportatore.  
  
 Per altre informazioni, vedere [definire vincoli di convalida per i modelli UML](../modeling/define-validation-constraints-for-uml-models.md).  
  
## <a name="menu-commands"></a>Comandi di menu  
 È possibile definire i comandi che gli utenti possono richiamare facendo clic con il pulsante destro del mouse sugli elementi in un diagramma UML. I comandi possono aggiornare il modello e i diagrammi o eseguire altre operazioni in [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
 Fabrikam definisce i comandi di menu per automatizzare le operazioni eseguite più di frequente, ad esempio creare un banco del check-in e connetterlo a un nastro trasportatore selezionato o ridisporre un diagramma in base alle regole di layout della società.  
  
 Visualizzare [definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
## <a name="gestures"></a>Movimenti  
 È possibile definire i comandi che gli utenti avviano facendo doppio clic su un elemento del diagramma o trascinando un diagramma o un elemento nel diagramma È possibile definire i comandi per la gestione di elementi trascinati da altri diagrammi UML, da altre parti di Visual Studio, da altre applicazioni o da Esplora risorse (o Esplora file).  
  
 I membri del team di Fabrikam possono associare un file, ad esempio una specifica, a qualsiasi elemento del modello trascinandolo dal desktop di Windows. Gli sviluppatori di strumenti hanno definito uno stereotipo che fornisce a qualsiasi elemento una proprietà del percorso del file e un movimento che imposta lo stereotipo e il percorso del file quando viene rilasciato un file su un elemento.  
  
 Per altre informazioni, vedere [definire un gestore movimenti in un diagramma di modellazione](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).  
  
## <a name="responding-to-changes"></a>Risposta alle modifiche  
 È possibile scrivere codice che risponda alle modifiche apportate al modello, sia per modifiche determinate da azioni dell'utente che da altro codice programma.  
  
 Gli sviluppatori di Fabrikam creano un codice che imposta automaticamente il colore di un elemento dipendente dal relativo stereotipo. Questo consente agli utenti di distinguere più facilmente i diversi ruoli svolti dagli elementi nei modelli.  
  
 Per altre informazioni, vedere [Procedura: Rispondere alle modifiche in un modello UML](../misc/how-to-respond-to-changes-in-a-uml-model.md).  
  
## <a name="model-bus"></a>Bus di modelli  
 Il bus di modelli consente di accedere a un diagramma o un modello da un altro diagramma o da un'altra estensione [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . Consente anche di distribuire le informazioni su più modelli, in modo tale che più persone possano lavorare contemporaneamente sul modello combinato.  
  
 Fabrikam usa gli elementi nei diagrammi di attività per rappresentare l'attrezzatura per la gestione dei bagagli. Ogni apparecchiatura può avere una specifica più dettagliata in un altro diagramma, che può trovarsi in un altro modello. I vincoli di convalida nel diagramma di flusso dei bagagli possono recuperare le proprietà rilevanti dell'attrezzatura da altri diagrammi. I riferimenti agli altri diagrammi vengono archiviati in proprietà aggiuntive definite negli stereotipi.  
  
 Per altre informazioni, vedere [integrare i modelli UML con altri modelli e strumenti](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
## <a name="generation"></a>Generazione  
 Da un modello è possibile generare codice programma, script, configurazioni, documenti, nuovi modelli o altri elementi.  
  
 Nei sistemi per la gestione dei bagagli progettati da Fabrikam, gran parte del codice programma è lo stesso per tutti i progetti. L'aspetto variabile principale è il piano del flusso dei bagagli nell'aeroporto. Quando il team di progettazione ha maturato esperienza con i primi progetti, gli sviluppatori di strumenti creano un modello che genera, a partire dal modello del flusso di bagagli, gran parte del codice programma variabile e altri file, ad esempio i documenti utente. In questo modo, il tempo di sviluppo e il tasso di errore in ogni nuovo progetto si riducono sensibilmente.  
  
 Per altre informazioni, vedere [generare file da un modello UML](../modeling/generate-files-from-a-uml-model.md).  
  
## <a name="team-foundation-server-integration"></a>Integrazione di Team Foundation Server  
 È possibile collegare elementi di lavoro agli elementi del modello e accedere agli elementi collegati a livello di codice.  
  
 Gli sviluppatori di strumenti di Fabrikam scrivono uno strumento che genera una pianificazione del lavoro per ogni progetto di aeroporto. Gli elementi di lavoro nella pianificazione sono collegati agli elementi del modello.  
  
 Per altre informazioni, vedere [definire un gestore di collegamento elemento di lavoro](../modeling/define-a-work-item-link-handler.md).  
  
## <a name="tools-that-update-models"></a>Strumenti di aggiornamento dei modelli  
 È possibile creare applicazioni autonome ed estensioni di Visual Studio che possono caricare modelli UML.  
  
 Gli sviluppatori di Fabrikam creano uno strumento che legge un modello e genera report dello stato di avanzamento del lavoro su ogni elemento del modello.  
  
 Per altre informazioni, vedere [leggere un modello UML nel codice programma](../modeling/read-a-uml-model-in-program-code.md).  
  
## <a name="domain-specific-languages"></a>Linguaggio specifico di dominio  
 Se si usa spesso un particolare tipo di modello, può essere utile creare un linguaggio specifico di dominio. Questa operazione può soddisfare le esigenze aziendali in modo migliore rispetto a un modello UML, ma richiede maggiori interventi a livello di compilazione e manutenzione. Per altre informazioni, vedere [Modeling SDK per Visual Studio - Domain-Specific Language](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).  
  
## <a name="external-resources"></a>Risorse esterne  
  
|**Categoria**|**Collegamenti**|  
|------------------|---------------|  
|**Video**|![collegamento a video](../data-tools/media/playvideo.gif "PlayVideo") [MSDN How Do I Series: Estendibilità e strumenti UML](http://go.microsoft.com/fwlink/?LinkId=214467)<br /><br /> ![collegamento a video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: UML con Visual Studio](http://go.microsoft.com/fwlink/?LinkId=199957)|  
|**Forum**|-   [Visual Studio Visualization and Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization and Modeling SDK (strumenti DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Blog**|[Blog di Visual Studi ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Articoli e pubblicazioni tecniche**|[MSDN Architecture Center](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>Vedere anche  
 [Creare modelli per l'app](../modeling/create-models-for-your-app.md)   
 [Riferimento API per l'estensibilità di modellazione UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
