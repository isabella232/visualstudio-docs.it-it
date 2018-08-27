---
title: Configurazione per l'Output del progetto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a02e331484abf2ef1450493d2ea1bdddaabe82bd
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42901184"
---
# <a name="project-configuration-for-output"></a>Configurazione del progetto per l'output
Ogni configurazione può supportare un set di processi di compilazione che generano gli elementi di output, ad esempio file eseguibile o una risorsa. Questi elementi di output sono privati per l'utente e possono essere inseriti in gruppi che si collegano i tipi correlati dell'output, ad esempio file eseguibili (.exe,. dll, con estensione LIB) e i file di origine (. idl, file con estensione h).  
  
 Gli elementi di output possono essere rese disponibili tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> metodi ed enumerate con il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> metodi. Quando si desidera raggruppare gli elementi di output, il progetto deve inoltre implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> interfaccia.  
  
 Il costrutto sviluppato implementando `IVsOutputGroup` consente ai progetti di raggruppare gli output in base all'utilizzo. Ad esempio, una DLL può essere raggruppata con il database di programma (PDB).  
  
> [!NOTE]
>  Un file PDB contiene le informazioni di debug e viene creata quando l'opzione 'Genera informazioni di Debug' è specificata quando si compila il file DLL o .exe. Il file con estensione PDB viene in genere generato per la configurazione di progetto di Debug solo.  
  
 Il progetto deve restituire lo stesso numero di gruppi per ogni configurazione supportata, anche se il numero degli output contenute all'interno di un gruppo può variare da una configurazione alla configurazione. Ad esempio, Matt del progetto DLL potrebbe includere mattd.dll e mattd.pdb nella configurazione di Debug, ma solo includere matt.dll nella configurazione delle vendite al dettaglio.  
  
 I gruppi dispongono inoltre le stesse informazioni di identificatore, ad esempio il nome canonico, nome visualizzato e informazioni di gruppo, dalla configurazione alla configurazione all'interno di un progetto. Questa coerenza consente la distribuzione e creazione di pacchetti per continuare a funzionare anche se le configurazioni di modifica.  
  
 Gruppi possono anche avere un output delle chiavi che consenta di tasti di scelta rapida creazione di pacchetti in modo da puntare in modo significativo. Qualsiasi gruppo potrebbe essere vuoto in una determinata configurazione, devono essere reso alcuna ipotesi sulla dimensione di un gruppo. La dimensione (numero di output) di ogni gruppo in qualsiasi configurazione può essere diversa dalla dimensione di un altro gruppo nella stessa configurazione. Può anche essere diversa dalla dimensione dello stesso gruppo in un'altra configurazione.  
  
 ![Rappresentazione grafica dei gruppi di output](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
Gruppi di output  
  
 L'uso primario del <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> interfaccia consiste nel fornire l'accesso per la compilazione, distribuzione e il debug di oggetti di gestione e consentire la libertà necessaria per raggruppare gli output di progetti. Per altre informazioni sull'uso di questa interfaccia, vedere [oggetto di configurazione progetto](../../extensibility/internals/project-configuration-object.md).  
  
 Nel diagramma precedente, compilato gruppo dispone di una chiave output tra le configurazioni (bD.exe o b.exe), pertanto l'utente può creare un collegamento a predefiniti e sapere che il collegamento funzionerà indipendentemente dalla configurazione distribuita. Origine del gruppo non è una chiave di output, in modo che l'utente non è possibile creare un collegamento ad esso. Se il gruppo di Debug compilata ha un output delle chiavi, ma il gruppo delle vendite al dettaglio compilato non, sarebbe un'implementazione non corretta. Di conseguenza, quindi, se qualsiasi configurazione dispone di un gruppo che non contiene alcun output, e, di conseguenza, nessun file di chiave e quindi altre configurazioni con il gruppo che contiene gli output non possono contenere i file di chiave. Gli editor di programma di installazione presuppongono che i nomi canonici e nomi visualizzati dei gruppi, nonché l'esistenza di un file di chiave, non modificare in base nelle configurazioni.  
  
 Si noti che se un progetto ha un `IVsOutputGroup` che non desidera creare un pacchetto o la distribuzione, è sufficiente non inserire tale output in un gruppo. L'output può comunque essere enumerato in genere implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> metodo che restituisce tutti gli output di una configurazione indipendentemente dal raggruppamento.  
  
 Per altre informazioni, vedere l'implementazione di `IVsOutputGroup` nell'esempio di un progetto personalizzato alla [MPF per i progetti](https://github.com/tunnelvisionlabs/MPFProj10).  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)   
 [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)   
 [Oggetto di configurazione progetto](../../extensibility/internals/project-configuration-object.md)   
 [Configurazione di soluzioni](../../extensibility/internals/solution-configuration.md)