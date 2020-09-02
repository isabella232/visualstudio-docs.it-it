---
title: Linee guida sul posizionamento del comando | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195096"
---
# <a name="command-placement-guidelines"></a>Linee guida per il posizionamento dei comandi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le procedure consigliate per posizionare i comandi in Visual Studio Integrated Development Environment (IDE) variano a seconda delle dimensioni del set di comandi. I comandi vengono definiti e posizionati in base alle informazioni contenute nei file con estensione vsct.  
  
## <a name="best-practices-for-all-command-sets"></a>Procedure consigliate per tutti i set di comandi  
 Per ogni set di comandi, attenersi alle seguenti linee guida:  
  
- Preparare in anticipo un grafico della struttura dei comandi. Identificare i comandi, le caselle combinate, i gruppi di comandi e i menu di scelta rapida che verranno utilizzati in più di una posizione.  
  
- I comandi visualizzati nello stesso gruppo devono essere correlati.  
  
- I gruppi che contengono un solo comando sono accettabili.  
  
- I pacchetti non devono aggiungere molti comandi ai menu esistenti di Visual Studio. Devono invece creare menu o sottomenu per ospitare i nuovi comandi.  
  
- Quando si inserisce un comando in un menu esistente, denominare il comando in modo che lo scopo sia chiaro e non verrà confuso con i comandi esistenti.  
  
## <a name="best-practices-for-small-command-sets"></a>Procedure consigliate per piccoli set di comandi  
 Se si sviluppa un pacchetto VSPackage con pochi comandi, attenersi anche alle linee guida seguenti:  
  
- Quando possibile, usare l' [elemento padre](../../extensibility/parent-element.md) di un comando, una casella combinata, un gruppo o un menu figlio per inserirlo nel gruppo appropriato.  
  
- Assegnare questi gruppi ai menu visualizzati dal pacchetto VSPackage.  
  
- L'elemento padre di un menu figlio o di un comando deve essere un [elemento di gruppo](../../extensibility/group-element.md). Assegnare i comandi e i menu figlio ai gruppi e quindi assegnare i gruppi ai menu padre.  
  
- È possibile inserire un comando in gruppi aggiuntivi aggiungendo una sezione dell' [elemento CommandPlacements](../../extensibility/commandplacements-element.md) dopo la definizione del comando e quindi aggiungendo all' `CommandPlacements Element` [elemento CommandPlacement](../../extensibility/commandplacement-element.md) per ogni gruppo aggiuntivo.  
  
## <a name="best-practices-for-large-command-sets"></a>Procedure consigliate per set di comandi di grandi dimensioni  
 Se il pacchetto VSPackage avrà molti comandi che verranno visualizzati in più contesti, attenersi anche alle linee guida seguenti:  
  
- Fare in modo che i menu, i gruppi e i comandi abbiano un elemento padre indipendente. Ovvero, non assegnare un oggetto `Parent Element` nella definizione dell'elemento.  
  
- Usare `CommandPlacement Element` le voci nella `CommandPlacements Element` sezione per inserire menu, gruppi e comandi nei rispettivi menu e gruppi padre.  
  
- Nella `CommandPlacements` sezione, le voci che popolano un determinato menu o gruppo devono essere adiacenti le une alle altre. Questa operazione facilita la leggibilità e rende `Priority` più semplice determinare le classificazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [File Visual Studio Command Table (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
