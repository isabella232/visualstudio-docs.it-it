---
title: Modifica e continuazione di modifiche non supportate in Visual Basic | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], unsupported method and property body edits
ms.assetid: 9b8fdc41-a193-49ad-ad72-dfcadd46f4b3
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ffe536b21b5569ad3427dfe4e3b281887cc00b13
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296322"
---
# <a name="unsupported-edits-in-visual-basic-edit-and-continue"></a>Modifiche non supportate in Modifica e continuazione di Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La funzionalità Modifica e continuazione consente di arrestare l'esecuzione del programma in modalità di interruzione, di apportare modifiche al codice in esecuzione e di riprendere l'esecuzione del programma con le modifiche recentemente incorporate. Le modifiche al codice dichiarativo che hanno effetto sulla struttura pubblica di una classe in genere non sono consentite, tuttavia alcune modifiche che potrebbe essere necessario apportare al corpo di una proprietà o di un metodo o a dichiarazioni private all'interno di una classe non sono consentite.  
  
 Se è necessario apportare una modifica non supportata, terminare il debug, apportare le modifiche e avviare una nuova sessione di debug.  
  
###  <a name="BKMK_MethodandPropertyBodyEdits"></a> Modifiche al corpo di proprietà e metodi  
 **Modifiche non supportate per le variabili locali statiche**: aggiunta o l'aggiornamento di una variabile locale o la rimozione di una variabile locale statica se questa può provocare un errore di compilazione.  
  
 **Modifiche non supportate per i Generics**: modifiche al metodo generico stesso o al corpo del metodo generico non sono supportate. È possibile aggiungere, eliminare o modificare istanze di un tipo generico o chiamate a metodi generici esistenti.  
  
 **Altre modifiche non supportate**  
  
-   Modifica dell'istruzione di chiamata a un metodo che si trova nello stack di chiamate.  
  
-   Aggiunta di un blocco `Try...Catch` quando il puntatore all'istruzione viene a trovarsi nel blocco `Catch` o nel blocco `Finally`.  
  
-   Rimozione di un `Try...Catch` blocco, quando il puntatore dell'istruzione è in un `Catch`blocco o `Finally` blocco.  
  
-   Aggiunta di un blocco `Using` intorno al puntatore all'istruzione corrente.  
  
-   Aggiunta di un blocco `SynchLock` intorno al puntatore all'istruzione corrente.  
  
###  <a name="BKMK_AttributeEdits"></a> Modifiche agli attributi  
 La funzionalità Modifica e continuazione non supporta la modifica degli attributi. In modo specifico, non supporta le modifiche seguenti:  
  
-   Definizione, modifica o eliminazione di una classe dell'attributo.  
  
-   Aggiunta di un attributo.  
  
-   Modifica o rimozione di un attributo esistente.  
  
###  <a name="BKMK_ClassDeclarationEdits"></a> Modifiche alle dichiarazioni di classe  
 La funzionalità Modifica e continuazione non consente di apportare la maggior parte delle modifiche alle dichiarazioni di classe quando è attivata la modalità di interruzione. In modo specifico, non supporta le modifiche seguenti:  
  
-   Ridenominazione, eliminazione o modifica dell'ereditarietà di una classe esistente.  
  
-   Implementazione di una nuova interfaccia o rimozione dell'implementazione di un'interfaccia.  
  
-   Modifica dei modificatori in una classe.  
  
-   Aggiunta, modifica o rimozione dello stato `ComClass`.  
  
-   Modifica di qualsiasi dichiarazione di classe generica.  
  
###  <a name="BKMK_ClassMemberDeclarationEdits"></a> Modifiche alle dichiarazioni di membro di classe  
 Le modifiche alle dichiarazioni dei membri sono proibite nella maggior parte dei casi con la funzionalità Modifica e continuazione. Ad esempio, non è possibile modificare la firma o il livello di accesso di un membro né rimuovere completamente membri se questi possono provocare un errore di compilazione. In modo specifico, non supporta le modifiche seguenti:  
  
-   Shadowing di una variabile membro esistente mediante dichiarazione di una variabile membro o globale con lo stesso nome nel blocco che la contiene.  
  
-   Shadowing di una variabile locale statica mediante dichiarazione di una nuova istanza all'interno di un blocco.  
  
-   Rimozione di gestori per un evento. L'aggiunta di un gestore dell'evento non è consentita.  
  
-   Aggiunta di un nuovo metodo o di una nuova proprietà di overload, a meno che la proprietà o il metodo non sia `Private` e non esistano occorrenze del nome nelle istruzioni attive.  
  
-   Aggiunta o rimozione della clausola `WithEvents` in una variabile membro.  
  
-   Eliminazione di un membro.  
  
-   Modifica della dichiarazione di una proprietà o di un metodo per interrompere l'implementazione di un'interfaccia.  
  
-   Modifica di qualsiasi metodo che utilizza generics.  
  
-   Modifica della firma o del tipo restituito di un metodo o di una proprietà non privata.  
  
-   Override o shadowing di un membro in una classe base.  
  
-   Aggiunta di un nuovo campo in qualsiasi classe contrassegnata con `SequentialLayout` o `ExplicitLayout`.  
  
-   Modifica dello stato `MustInherit` o `NotOverridable` di un metodo.  
  
-   Modifica dei modificatori di accesso per una proprietà o un metodo.  
  
-   Modifica del tipo o dello stato di sola lettura di un campo.  
  
-   Modifica di un campo pubblico.  
  
###  <a name="BKMK_CompilerOptionEdits"></a> Modifiche alle opzioni del compilatore  
 Quando si utilizza la funzionalità Modifica e continuazione in modalità di interruzione, non è possibile modificare, aggiungere o rimuovere le seguenti opzioni del compilatore:  
  
-   **Option Strict**  
  
-   **Option Explicit**  
  
-   **Option Compare**  
  
###  <a name="BKMK_ConstantsEdits"></a> Modifiche alle costanti  
 Le modifiche che è possibile apportare alle costanti con la funzionalità Modifica e continuazione sono soggette a numerose limitazioni. In modo specifico, non supporta le modifiche seguenti:  
  
-   Aggiunta o aggiornamento di una variabile costante.  
  
-   Modifica del tipo o del valore di una costante.  
  
-   Rimozione di una costante.  
  
###  <a name="BKMK_DelegateandEventDeclarationEdits"></a> Modifiche alle dichiarazioni di evento e delegato  
 L'applicazione di modifiche a delegati ed eventi non è consentita dalla funzionalità Modifica e continuazione quando è attiva la modalità interruzione. In modo specifico, non supporta le modifiche seguenti:  
  
-   Modifica o eliminazione di una definizione di delegato.  
  
-   Eliminazione di un evento.  
  
###  <a name="BKMK_EnumerationEdits"></a> Modifiche alle enumerazioni  
 Le modifiche alle enumerazioni (`Enums`) non sono consentite con la funzionalità Modifica e continuazione quando è attivata la modalità di interruzione. In modo specifico, non supporta le modifiche seguenti:  
  
-   Modifica del tipo sottostante di una `Enum`.  
  
-   Aggiunta, modifica o rimozione di un membro `Enum`.  
  
-   Modifica del modificatore di accesso di una `Enum`.  
  
###  <a name="BKMK_ExternalDeclarationsEdits"></a> Modifiche alle dichiarazioni esterne  
 In generale, non è consentito modificare le dichiarazioni di metodi esterni con la funzionalità Modifica e continuazione. In modo specifico, non supporta le modifiche seguenti:  
  
-   Aggiunta o rimozione di una dichiarazione esterna.  
  
-   Modifica degli attributi di firma o marshalling di una dichiarazione esterna.  
  
###  <a name="BKMK_ImportsEdits"></a> Modifiche a Imports  
 La funzionalità Modifica e continuazione non consente di aggiungere, modificare o rimuovere istruzioni `Imports` quando è attivata la modalità di interruzione.  
  
###  <a name="BKMK_InterfaceDefinitionEdits"></a> Modifiche alle definizioni di interfaccia  
 Sebbene sia spesso possibile apportare modifiche a membri che implementano interfacce, le modifiche alle definizioni delle interfacce in genere non sono consentite con la funzionalità Modifica e continuazione. In modo specifico, non supporta le modifiche seguenti:  
  
-   Aggiunta, modifica o rimozione di membri di interfaccia.  
  
-   Eliminazione di un'interfaccia esistente.  
  
-   Modifica del modificatore di accesso di un'interfaccia.  
  
-   Modifica della gerarchia di ereditarietà di un'interfaccia.  
  
###  <a name="BKMK_ModuleDeclarationEdits"></a> Modifiche alle dichiarazioni di modulo  
 La funzionalità Modifica e continuazione non supporta la maggior parte delle modifiche alle dichiarazioni di modulo quando è attivata la modalità di interruzione. In modo specifico, non supporta le modifiche seguenti:  
  
-   Creazione di un nuovo modulo.  
  
-   Ridenominazione o eliminazione di un modulo esistente.  
  
-   Modifica del modificatore di accesso di un modulo.  
  
###  <a name="BKMK_ModuleMemberDeclarationEdits"></a> Modifiche alle dichiarazioni di membri di modulo  
 La funzionalità Modifica e continuazione consente di apportare varie modifiche ai membri di modulo, ovvero proprietà, metodi e campi quando è attivata la modalità di interruzione. Alcune modifiche non sono, tuttavia supportate. In particolare, la funzionalità Modifica e continuazione non supporta l'aggiunta, l'eliminazione o la modifica del tipo o della firma di alcun membro.  
  
 In modo specifico, non supporta le modifiche seguenti:  
  
-   Aggiunta di un nuovo membro, a meno che non esistano occorrenze del nome nelle istruzioni attive.  
  
-   Rimozione di una proprietà o di un metodo.  
  
-   Modifica della firma di una proprietà o di un metodo.  
  
-   Aggiunta, ridenominazione, spostamento o eliminazione di un campo.  
  
-   Modifica di qualsiasi metodo che utilizza generics.  
  
-   Modifica dei modificatori di accesso per una proprietà o un metodo, ad esempio modifica di `Public` in `Private`.  
  
-   Eliminazione o modifica del tipo di un campo esistente.  
  
###  <a name="BKMK_NestedTypeDeclarationEdits"></a> Modifiche alle dichiarazioni di tipo annidato  
 La funzionalità Modifica e continuazione non supporta lo spostamento di un tipo annidato in un altro spazio dei nomi o tipo.  
  
###  <a name="BKMK_StructureDeclarationEdits"></a> Modifiche alle dichiarazioni di struttura  
 La maggior parte delle modifiche alle dichiarazioni di struttura non sono consentite dalla modifica e continuazione durante **Interrompi** modalità. In modo specifico, non supporta le modifiche seguenti:  
  
-   Ridenominazione o eliminazione di una struttura esistente.  
  
-   Implementazione di una nuova interfaccia o rimozione dell'implementazione di un'interfaccia.  
  
-   Modifica del modificatore di accesso di una struttura.  
  
###  <a name="BKMK_StructureMemberDeclarationEdits"></a> Modifiche alle dichiarazioni di membro di struttura  
 La funzionalità Modifica e continuazione consente di apportare varie modifiche ai membri di struttura, ovvero proprietà, metodi e campi, quando è attivata la modalità di interruzione. Alcune modifiche, tuttavia, tra cui quelle che influiscono sulla dichiarazione dei membri di struttura, non sono consentite. In modo specifico, non supporta le modifiche seguenti:  
  
-   Rimozione di una proprietà o di un metodo.  
  
-   Aggiunta o rimozione di un campo.  
  
-   Modifica della firma di una proprietà o di un metodo.  
  
-   Modifica di qualsiasi metodo che utilizza generics.  
  
-   Modifica dell'impostazione in base alla quale una dichiarazione di proprietà o metodo implementa o meno un'interfaccia.  
  
-   Modifica dei modificatori di accesso di una proprietà o metodo (ad esempio, modificando `Public` per **privato**).  
  
-   Rimozione di un campo.  
  
-   Modifica del tipo di un campo.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: applicare modifiche in modalità di interruzione con modifica e continuazione](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)   
 [Modifica e continuazione (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)



