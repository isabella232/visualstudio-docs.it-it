---
title: Linee guida per la selezione host di comando | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5d88a477403c98ff11c5f7303b55f5eb713b668c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195096"
---
# <a name="command-placement-guidelines"></a>Linee guida per il posizionamento dei comandi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le procedure consigliate per il posizionamento comandi nell'ambiente di sviluppo integrato (IDE) di Visual Studio variano a seconda delle dimensioni del set di comandi. I comandi sono definiti e posizionati in base alle informazioni nei file con estensione vsct.  
  
## <a name="best-practices-for-all-command-sets"></a>Procedure consigliate per tutti i set di comandi  
 Per ogni set di comandi e seguire queste linee guida:  
  
- Preparare in anticipo un grafico della struttura del comando. Identificare i comandi, caselle combinate, gruppi di comandi e menu di scelta rapida che verranno usati in più posizioni.  
  
- I comandi che vengono visualizzati nello stesso gruppo devono essere correlati.  
  
- I gruppi che contengono un unico comando sono accettabili.  
  
- I pacchetti consigliabile non aggiungere un numero elevato di comandi a menu di Visual Studio esistenti. Invece, è necessario creare menu o sottomenu per ospitare i nuovi comandi.  
  
- Quando un comando è inserire in un menu esistente, nome del comando in modo che il suo scopo sia chiaro e non essere confuso con i comandi esistenti.  
  
## <a name="best-practices-for-small-command-sets"></a>Le procedure consigliate per i set di piccole dimensioni comando  
 Se si sta sviluppando un pacchetto VSPackage che dispone di alcuni comandi, anche seguire queste linee guida:  
  
- Quando possibile, usare il [elemento padre](../../extensibility/parent-element.md) di un comando, casella combinata, gruppo o menu figlio per mettere in pratica il gruppo appropriato.  
  
- Assegnare questi gruppi di menu da visualizzare dal pacchetto VSPackage.  
  
- L'elemento padre di un menu figlio o un comando deve essere un [elemento gruppo](../../extensibility/group-element.md). Assegnare ai gruppi di comandi e i menu figlio e quindi assegnare i gruppi ai menu padre.  
  
- È possibile inserire un comando in altri gruppi aggiungendo un [elemento CommandPlacements](../../extensibility/commandplacements-element.md) sezione dopo la definizione del comando, quindi aggiungere il `CommandPlacements Element` una [elemento CommandPlacement](../../extensibility/commandplacement-element.md) per ognuno gruppo aggiuntivo.  
  
## <a name="best-practices-for-large-command-sets"></a>Le procedure consigliate per i set di grandi dimensioni comando  
 Se il pacchetto VSPackage avrà molti comandi che verranno visualizzati in più contesti, è necessario seguire anche queste linee guida:  
  
- Rendere i menu, gruppi e i comandi self-padre. Vale a dire, non si assegna un `Parent Element` nella definizione dell'elemento.  
  
- Uso `CommandPlacement Element` voci nel `CommandPlacements Element` sezione per inserire i menu, gruppi e i comandi nei menu del padre e i gruppi.  
  
- Nel `CommandPlacements` sezione, le voci che popolano un determinato menu o il gruppo deve essere adiacente tra loro. Ciò agevola la leggibilità e rende il `Priority` più semplice determinare le classificazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [File Visual Studio Command Table (VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
