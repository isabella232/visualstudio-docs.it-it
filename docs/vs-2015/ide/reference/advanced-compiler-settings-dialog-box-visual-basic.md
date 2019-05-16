---
title: Finestra di dialogo Impostazioni del compilatore avanzate (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
caps.latest.revision: 52
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4f98d2209ca3a2869e4be69a9c46faa5c4755a06
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699917"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Finestra di dialogo Impostazioni del compilatore avanzate (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Per specificare le proprietà di configurazione avanzate della build del progetto, usare la finestra di dialogo **Impostazioni del compilatore avanzate** di **Creazione progetti**. Questa finestra di dialogo si applica esclusivamente ai progetti Visual Basic.  
  
### <a name="to-access-this-dialog-box"></a>Per accedere a questa finestra di dialogo  
  
1. In **Esplora soluzioni** scegliere un nodo progetto, non il nodo **Soluzione**.  
  
2. Scegliere **Proprietà** dal menu **Progetto**. Quando viene visualizzata la finestra **Creazione progetti**, fare clic sulla scheda **Compilazione**.  
  
3. Nella [Pagina Compilazione, Creazione progetti (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) selezionare la **configurazione** e la **piattaforma**. Nelle configurazioni della build semplificate gli elenchi **Configurazione** e **Piattaforma** non vengono visualizzati. Per altre informazioni, vedere [Debug and Release Project Configurations](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) (Eseguire il debug e il rilascio delle configurazione del progetto).  
  
4. Fare clic su **Opzioni di compilazione avanzate**.  
  
   [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="optimizations"></a>Ottimizzazioni  
 Le opzioni seguenti specificano le ottimizzazioni che in alcuni casi consentono di ridurre le dimensioni di un file di programma, velocizzare l'esecuzione di un programma o accelerare il processo di compilazione.  
  
 **Rimuovi controllo dell'overflow di Integer**  
 Per impostazione predefinita, questa casella di controllo è deselezionata per abilitare il controllo dell'overflow di Integer. Selezionare questa casella di controllo per rimuovere il controllo dell'overflow di Integer. Se si seleziona questa casella di controllo, i calcoli Integer potrebbero risultare più veloci. Tuttavia, se si rimuove il controllo dell'overflow e si verifica un overflow delle capacità del tipo di dati, potrebbero venire archiviati risultati non corretti senza la generazione di un errore.  
  
 Se le condizioni di overflow vengono controllate e si verifica l'overflow di un'operazione con valori integer, verrà generata un'eccezione <xref:System.OverflowException>. Se le condizioni di overflow non vengono controllate, eventuali overflow di operazioni con valori integer non generano alcuna eccezione.  
  
 **Abilita ottimizzazioni**  
 Per impostazione predefinita, questa casella di controllo è deselezionata per disabilitare le ottimizzazioni del compilatore. Selezionare questa casella di controllo per abilitare le ottimizzazioni del compilatore. Le ottimizzazioni del compilatore consentono di ridurre le dimensioni del file di output rendendolo più veloce ed efficiente. Tuttavia, poiché le ottimizzazioni comportano la riorganizzazione del codice nel file di output, le operazioni di debug possono risultare più complesse.  
  
 **Indirizzo di base DLL**  
 In questa casella di testo viene visualizzato l'indirizzo di base DLL predefinito in formato esadecimale. Nei progetti Libreria di classi e Libreria di controlli è possibile usare questa casella di testo per specificare l'indirizzo di base da usare quando viene creata la DLL.  
  
 **Genera informazioni di debug**  
 Selezionare **Nessuna**, **Completa** o **pdb-only** (solo PDB) dall'elenco. **Nessuna** specifica che non saranno generate informazioni di debug. **Completa** specifica che verranno generate informazioni di debug complete e **pdb-only** (solo PDB) specifica che verranno generate solo informazioni di debug PDB. Per impostazione predefinita, questa opzione è impostata su **Completa**.  
  
## <a name="compilation-constants"></a>Costanti di compilazione  
 Le costanti di compilazione condizionale producono un effetto simile all'uso di una direttiva per il preprocessore [#Const](https://msdn.microsoft.com/library/707669e5-23f9-4f17-8622-a0d534429386) in un file di origine, ad eccezione del fatto che le costanti definite sono pubbliche e si applicano a tutti i file del progetto. È possibile usare le costanti di compilazione condizionale insieme alla direttiva [#If...Then...#Else](https://msdn.microsoft.com/library/10bba104-e3fd-451b-b672-faa472530502) per compilare i file di origine in modo condizionale. Vedere [Conditional Compilation](https://msdn.microsoft.com/library/9c35e55e-7eee-44fb-a586-dad1f1884848) (Compilazione condizionale).  
  
 **Definisci costante DEBUG**  
 Per impostazione predefinita, questa casella di controllo è selezionata e specifica che deve essere impostata una costante DEBUG.  
  
 **Definisci costante TRACE**  
 Per impostazione predefinita, questa casella di controllo è selezionata e specifica che deve essere impostata una costante TRACE.  
  
 **Costanti personalizzate**  
 Immettere le costanti personalizzate per l'applicazione in questa casella di testo. Le voci devono essere delimitate da virgole usando questa forma: **Nome1="Valore1",Nome2="Valore2",Nome3="Valore3"**.  
  
## <a name="other-settings"></a>Altre impostazioni  
 **Genera assembly di serializzazione**  
 Questa impostazione specifica se il compilatore creerà assembly di serializzazione XML. Gli assembly di serializzazione possono migliorare le prestazioni di avvio della classe <xref:System.Xml.Serialization.XmlSerializer>, se è stata usata per serializzare i tipi nel codice. Per impostazione predefinita, questa opzione è impostata su **Auto**. Specifica quindi che saranno generati assembly di serializzazione solo se è stata usata la classe <xref:System.Xml.Serialization.XmlSerializer> per codificare i tipi nel codice in XML. **Off** specifica che non saranno mai generati assembly di serializzazione, indipendentemente dal fatto che il codice usi o meno la classe <xref:System.Xml.Serialization.XmlSerializer>. **On** specifica che saranno sempre generati assembly di serializzazione. Gli assembly di serializzazione sono denominati `TypeName`.XmlSerializers.dll.  
  
## <a name="see-also"></a>Vedere anche  
 [Pagina Compilazione, Creazione progetti (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
