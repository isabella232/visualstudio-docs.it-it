---
title: Stereotipi standard per modelli UML | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML, stereotypes
- UML diagrams, stereotypes
ms.assetid: 8a8c2321-1cae-4ba8-bb9e-23495c3404d8
caps.latest.revision: 22
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3e5cabed5b2b75d9a97c74dd58d87ea387df8f8e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527617"
---
# <a name="standard-stereotypes-for-uml-models"></a>Stereotipi standard per modelli UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [stereotipi Standard per modelli UML](https://docs.microsoft.com/visualstudio/modeling/standard-stereotypes-for-uml-models).  
  
È possibile aggiungere stereotipi a elementi del modello UML per fornire altre informazioni a chi legge o al computer per l'elaborazione. Gli stereotipi vengono definiti nei profili e ogni profilo fornisce un set di stereotipi. Alcuni profili vengono forniti con Visual Studio. Si possono anche definire i propri profili che possono contenere stereotipi personalizzati. Per altre informazioni, vedere [definire un profilo per estendere UML](../modeling/define-a-profile-to-extend-uml.md).  
  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="the-standard-profiles"></a>Profili standard  
 I profili seguenti sono disponibili in un'edizione supportata di Visual Studio, non appena è stato installato.  
  
|Profilo|Scopo|  
|-------------|-------------|  
|[Profilo Standard UML L2](#L2)|Set standard di stereotipi che possono essere usati per aggiungere altre informazioni su un elemento o una relazione.|  
|[Profilo Standard UML L3](#L3)|Set standard di stereotipi che possono essere usati per aggiungere altre informazioni su un elemento o una relazione.|  
|[Profilo c#](#NetProfile)|Se si vuole che una classe o un altro elemento in un modello UML rappresenti il codice programma, è possibile indicarlo applicando uno degli stereotipi del profilo C#.<br /><br /> Questi stereotipi inoltre aggiungono le proprietà agli elementi del modello.|  
  
 Quando si crea un nuovo modello UML, i profili standard UML L2 e L3 vengono collegati al modello, a meno che non si rimuovano i collegamenti.  
  
 Per usare gli stereotipi in uno di questi profili, prima è necessario collegare il profilo a un pacchetto o a un modello contenente gli elementi a cui applicarli.  
  
#### <a name="to-link-a-profile-to-a-model-or-a-package"></a>Per collegare un profilo a un modello o a un pacchetto  
  
1.  Aprire **Esplora modelli UML**. Nel **architettura** dal menu **Windows**, quindi fare clic su **Esplora modelli UML**.  
  
2.  Individuare un pacchetto o un modello contenente tutti gli elementi a cui applicare gli stereotipi nel profilo.  
  
3.  Fare doppio clic il pacchetto o il modello e quindi fare clic su **proprietà**.  
  
4.  Nel **proprietà** impostare nella finestra di **profili** proprietà per i profili desiderati.  
  
#### <a name="to-remove-the-link-between-a-profile-and-a-model-or-package"></a>Per rimuovere il collegamento tra un profilo e un modello o un pacchetto  
  
1.  In Esplora modelli UML, fare clic sul pacchetto o sul modello e quindi fare clic su **proprietà**.  
  
2.  Nella finestra Proprietà impostare il **profili** proprietà vuoto.  
  
    > [!NOTE]
    >  È possibile scollegare un profilo solo se nessuno degli elementi nel modello o nel pacchetto usa gli stereotipi del profilo.  
  
#### <a name="to-apply-a-stereotype-to-a-model-element"></a>Per applicare uno stereotipo a un elemento del modello  
  
1.  Fare doppio clic sull'elemento del modello in un diagramma o nel **Esplora modelli UML**, quindi fare clic su **proprietà**.  
  
2.  Scegliere il **stereotipi** proprietà e selezionare gli stereotipi che si desidera applicare.  
  
     Gli stereotipi selezionati vengono visualizzati tra «frecce di espansione» nell'elemento del modello, per la maggior parte dei tipi di elemento.  
  
    > [!NOTE]
    >  Se non è possibile visualizzare il **stereotipi** proprietà, o se lo stereotipo desiderato non viene visualizzata, verificare che l'elemento del modello si trova all'interno di un pacchetto o un modello a cui è stato collegato il profilo appropriato.  
  
3.  Alcuni stereotipi consentono di impostare i valori di altre proprietà per l'elemento del modello. Per visualizzare queste proprietà, espandere la **stereotipi** proprietà.  
  
###  <a name="L2"></a> Profilo Standard UML L2  
 I seguenti stereotipi possono essere usati per specializzare il significato degli elementi del modello UML, a meno che il collegamento al profilo non sia stato rimosso dal modello.  
  
 Il significato esatto di questi stereotipi è determinato dalle convenzioni locali e dagli strumenti che potrebbero essere usati per elaborare il modello.  
  
|Stereotipo|Si applica a|Significato|  
|----------------|----------------|-------------|  
|ausiliario|Classe|Classe che supporta un'altra classe, in genere implementando la logica aggiuntiva. L'altra classe potrebbe avere lo stereotipo «focus».|  
|chiama|Dipendenza|La classe client chiama le operazioni del fornitore.|  
|crea|Dipendenza|La classe client crea le istanze del fornitore.|  
|crea|Messaggio|Il mittente crea il ricevitore.|  
|crea|Operazione|Questa operazione è un costruttore.|  
|deriva|Dipendenza|L'elemento client viene calcolato completamente o parzialmente dal fornitore.|  
|elimina|Operazione|L'operazione elimina l'istanza.|  
|documento|Elemento|«file» che non è un'origine o un eseguibile.|  
|entità|Componente|Il componente rappresenta un concetto di business.|  
|eseguibile|Elemento|«file» eseguibile.|  
|file|Elemento|File fisico.|  
|stato attivo|Classe|Classe che definisce la logica di business principale, supportata da diverse classi «auxiliary».|  
|framework|Package|Questo pacchetto definisce uno schema progettuale riutilizzabile.|  
|implementa|Componente|Implementazione di uno stereotipo «specification».|  
|implementationClass|Classe|La classe descrive un'implementazione e ogni istanza di runtime dispone di una classe di implementazione fissa. Si differenzia da «type».|  
|crea istanza|Dipendenza|Il client crea le istanze del fornitore.|  
|libreria|Elemento|«file» di libreria.|  
|metaclass|Classe|Anche le istanze di questa classe sono classi.|  
|modelLibrary|Package|Contiene gli elementi del modello che devono essere riutilizzati dai pacchetti da importare. In genere è definito come parte di un profilo e importato automaticamente dall'applicazione del profilo.|  
|processo|Componente|Componente basato sulle transazioni o che contiene un thread.|  
|realizzazione|Classe, interfaccia, componente|Descrive un'implementazione.|  
|rifinisci|Dipendenza|La classe, il componente o il pacchetto client offre più informazioni del fornitore sulla specifica o sulla progettazione.|  
|responsabilità|Dipendenza|Il commento dal lato fornitore della dipendenza definisce le responsabilità della classe o del componente client.|  
|script|Elemento|«file» interpretabile.|  
|invia|Dipendenza|L'operazione di origine invia il segnale di destinazione.|  
|servizio|Componente|Componente senza stato.|  
|origine|Elemento|«file» compilabile.|  
|specificazione|Classe, interfaccia, componente|Definisce il comportamento di un componente o di un oggetto senza definire come funziona internamente.|  
|sottosistema|Componente|Parte di un sistema di grandi dimensioni. Un sottosistema in un diagramma caso di utilizzo è un componente con lo stereotipo subsystem.|  
|traccia|Dipendenza|L'elemento client fa parte della progettazione che realizza il fornitore. Le due estremità di questa dipendenza sono in genere in modelli diversi. Uno di questi modelli è una realizzazione dell'altro.|  
|tipo|Classe|Specifica il comportamento di un oggetto senza indicare come viene implementato. Un oggetto è un membro di un tipo se è conforme alla specifica.|  
|utilità|Classe|Raccolta di funzioni statiche. La classe non dispone di istanze.|  
  
###  <a name="L3"></a> Profilo Standard UML L3  
 I seguenti stereotipi possono essere usati per specializzare il significato degli elementi del modello UML, a meno che il profilo non sia stato scollegato dal modello.  
  
 Il significato esatto di questi stereotipi è determinato dalle convenzioni locali e dagli strumenti che potrebbero essere usati per elaborare il modello.  
  
|Stereotipo|Si applica a|Descrizione|  
|----------------|----------------|-----------------|  
|buildComponent|Componente|Raccolta di elementi usati per definire una build.|  
|metaModel|Modello|Definisce un linguaggio di modellazione, ad esempio una variante di UML, o un linguaggio specifico del dominio.|  
|systemModel|Modello|Modello che è una raccolta di modelli che si applicano allo stesso sistema, ad esempio una specifica, una realizzazione e le relazioni di traccia reciproche.|  
  
##  <a name="NetProfile"></a> Profilo c#  
 Gli stereotipi definiti in questo profilo consentono di indicare che un elemento del modello verrà tradotto in codice programma. Ogni stereotipo definisce proprietà aggiuntive che è possibile impostare nell'elemento del modello.  
  
 Per rendere disponibili questi stereotipi, collegare un modello o un pacchetto al profilo C#. È quindi possibile applicare gli stereotipi agli elementi del modello in tale modello o pacchetto.  
  
 Gli stereotipi disponibili, gli elementi a cui si applicano e le altre proprietà rese disponibili sono riepilogati nella tabella seguente.  
  
|Stereotipo|Si applica a|Proprietà|  
|----------------|----------------|----------------|  
|**Classe c#**|Classe UML<br /><br /> Componente|**Attributi CLR**<br /><br /> **È parziale**<br /><br /> **È Sealed**<br /><br /> **È statico**<br /><br /> **Non è sicuro**<br /><br /> **Visibilità del pacchetto**|  
|**Struct c#**|Classe UML<br /><br /> Componente|**Attributi CLR**<br /><br /> **È parziale**<br /><br /> **Non è sicuro**<br /><br /> **Visibilità del pacchetto**|  
|**Membri globali c#**|Classe UML<br /><br /> Componente|**Attributi CLR**|  
|**Interfaccia c#**|Interfaccia UML|**Attributi CLR**<br /><br /> **È parziale**<br /><br /> **Visibilità del pacchetto**|  
|**Enum in c#**|Enumerazione UML|**ClrAttributes**<br /><br /> **Tipo di base**|  
|**Spazio dei nomi c#**|Pacchetto UML|**Attributi CLR**<br /><br /> **Nome di base**<br /><br /> **Uso degli spazi dei nomi**|  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere stereotipi a elementi del modello UML](../modeling/add-stereotypes-to-uml-model-elements.md)   
 [Personalizzare il modello con profili e stereotipi](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [Definire un profilo per estendere UML](../modeling/define-a-profile-to-extend-uml.md)



