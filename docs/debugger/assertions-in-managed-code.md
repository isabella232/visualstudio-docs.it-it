---
title: Asserzioni nel codice gestito | Microsoft Docs
description: Informazioni sulle asserzioni come strumento di debug per codice gestito C#, Visual Basic o F# in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], assertions in managed code
- Trace.Assert method
- debugging managed code, assertions
- Debug.Assert method
- Debug.Listeners property
- assertions, side effects
- Trace.Listeners property
- assertions, managed code
ms.assetid: 70ab2522-6486-4076-a1a9-e0f11cd0f3a1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- dotnet
ms.openlocfilehash: 937c6474aab6ea1171eccf6914e4e850a8e4bb3b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122129870"
---
# <a name="assertions-in-managed-code"></a>Asserzioni nel codice gestito
Un'asserzione, o istruzione `Assert`, verifica una condizione specificata come argomento dell'istruzione `Assert`. Se la condizione restituisce true, non viene eseguita alcuna azione. Se restituisce false, l'asserzione ha esito negativo. Se l'esecuzione avviene all'interno di una build di debug, viene attivata la modalità di interruzione.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> In questo argomento
 [Asserzioni nello spazio dei nomi System.Diagnostics](#BKMK_Asserts_in_the_System_Diagnostics_Namespace)

 [Metodo Debug.Assert](#BKMK_The_Debug_Assert_method)

 [Effetti collaterali di Debug.Assert](#BKMK_Side_effects_of_Debug_Assert)

 [Requisiti di traccia e debug](#BKMK_Trace_and_Debug_Requirements)

 [Argomenti assert](#BKMK_Assert_arguments)

 [Personalizzazione del comportamento del metodo Assert](#BKMK_Customizing_Assert_behavior)

 [Impostazione di asserzioni nei file di configurazione](#BKMK_Setting_assertions_in_configuration_files)

## <a name="asserts-in-the-systemdiagnostics-namespace"></a><a name="BKMK_Asserts_in_the_System_Diagnostics_Namespace"></a> Asserzioni nello spazio dei nomi System.Diagnostics
 In Visual Basic e Visual C# è possibile utilizzare il metodo `Assert` da <xref:System.Diagnostics.Debug> o <xref:System.Diagnostics.Trace>che si trovano nello spazio dei nomi <xref:System.Diagnostics>. I metodi della classe <xref:System.Diagnostics.Debug> non sono inclusi in una versione di rilascio del programma, pertanto non aumentano le dimensioni né riducono la velocità del codice di rilascio.

 C++ non supporta i metodi della classe <xref:System.Diagnostics.Debug>. È possibile ottenere lo stesso effetto utilizzando la classe <xref:System.Diagnostics.Trace> con compilazione condizionale, ad esempio `#ifdef DEBUG`... `#endif`.

 [Contenuto dell'argomento](#BKMK_In_this_topic)

## <a name="the-debugassert-method"></a><a name="BKMK_The_Debug_Assert_method"></a> Metodo Debug.Assert
 Utilizzare il metodo <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> per verificare le condizioni che devono restituire true se il codice è corretto. Si supponga, ad esempio, di aver scritto una funzione di divisione per interi. In base alle regole matematiche, il divisore non può mai essere zero. A tale scopo, utilizzare un'asserzione:

```VB
Function IntegerDivide(ByVal dividend As Integer, ByVal divisor As Integer) As Integer
    Debug.Assert(divisor <> 0)
    Return CInt(dividend / divisor)
End Function
```

```csharp
int IntegerDivide ( int dividend , int divisor )
{
    Debug.Assert ( divisor != 0 );
    return ( dividend / divisor );
}
```

 Quando si esegue questo codice nel debugger, l'istruzione di asserzione viene valutata, ma nella versione di rilascio il confronto non viene eseguito, pertanto non viene generato alcun sovraccarico aggiuntivo.

 Di seguito è riportato un altro esempio. Si supponga che esista una classe che implementa un conto corrente:

```VB
Dim amount, balance As Double
balance = savingsAccount.balance
Debug.Assert(amount <= balance)
SavingsAccount.Withdraw(amount)
```

```csharp
float balance = savingsAccount.Balance;
Debug.Assert ( amount <= balance );
savingsAccount.Withdraw ( amount );
```

 Prima di prelevare denaro dal conto, si desidera verificare che il saldo sia sufficiente a coprire la somma di denaro che si intende ritirare. Per controllare il saldo, è possibile scrivere un'asserzione:

```VB
Dim amount, balance As Double
balance = savingsAccount.balance
Trace.Assert(amount <= balance)
SavingsAccount.Withdraw(amount)
```

```csharp
float balance = savingsAccount.Balance;
Trace.Assert ( amount <= balance );
savingsAccount.Withdraw ( amount );
```

 Le chiamate al metodo <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> scompaiono quando si crea una versione di rilascio del codice. Ciò significa che nella versione di rilascio la chiamata che controlla il saldo scompare. Per risolvere questo problema, sostituire <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> con <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, che non scompare nella versione di rilascio:

 A differenza dalle chiamate a <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, le chiamate a <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> comportano un sovraccarico nella versione di rilascio.

 [Contenuto dell'argomento](#BKMK_In_this_topic)

## <a name="side-effects-of-debugassert"></a><a name="BKMK_Side_effects_of_Debug_Assert"></a> Effetti secondari di Debug.Assert
 Quando si utilizza <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>, assicurarsi che il codice contenuto in `Assert` non modifichi i risultati del programma se `Assert` viene rimosso. In caso contrario, si potrebbe introdurre accidentalmente un bug che si manifesta solo nella versione di rilascio del programma. Prestare particolare attenzione alle asserzioni contenenti chiamate di funzioni o procedure, come quella del seguente esempio:

```VB
' unsafe code
Debug.Assert (meas(i) <> 0 )
```

```csharp
// unsafe code
Debug.Assert (meas(i) != 0 );
```

 Questo utilizzo di <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> potrebbe sembrare sicuro a una prima analisi, ma si supponga che la funzione meas aggiorni un contatore ogni volta che viene chiamata. Quando si compila la versione di rilascio, la chiamata a meas viene eliminata, pertanto il contatore non viene aggiornato. Questo è un esempio di funzione con un effetto collaterale. L'eliminazione di una chiamata a una funzione che produce effetti collaterali potrebbe comportare la generazione di un bug che si manifesta solo nella versione di rilascio. Per evitare questo tipo di problema, non inserire chiamate di funzione in un'istruzione <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>, Utilizzare invece una variabile temporanea:

```VB
temp = meas( i )
Debug.Assert (temp <> 0)
```

```csharp
temp = meas( i );
Debug.Assert ( temp != 0 );
```

 Anche quando si utilizza <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, evitare di inserire chiamate di funzione all'interno di un'istruzione `Assert`. Queste chiamate non dovrebbero presentare rischi in quanto le istruzioni <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> non vengono eliminate nella build di rilascio. Se tuttavia si cerca di evitare sempre tali costrutti, è meno probabile che si commetta un errore quando si utilizza <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.

 [Contenuto dell'argomento](#BKMK_In_this_topic)

## <a name="trace-and-debug-requirements"></a><a name="BKMK_Trace_and_Debug_Requirements"></a> Requisiti di traccia e debug
 Se si crea un progetto utilizzando le procedure guidate di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], per impostazione predefinita il simbolo TRACE viene definito in entrambe le configurazioni di rilascio e di debug. Il simbolo DEBUG viene definito per impostazione predefinita solo nella build di debug.

 In caso contrario, affinché i metodi <xref:System.Diagnostics.Trace> funzionino correttamente, è necessario che all'inizio del file di origine del programma sia presente una delle seguenti:

- `#Const TRACE = True` in Visual Basic

- `#define TRACE` in Visual C# e C++

  In alternativa, è necessario che il programma venga compilato con l'opzione TRACE:

- `/d:TRACE=True` in Visual Basic

- `/d:TRACE` in Visual C# e C++

  Per utilizzare i metodi Debug in una build di rilascio di C# o Visual Basic, è necessario definire il simbolo DEBUG nella configurazione di rilascio.

  C++ non supporta i metodi della classe <xref:System.Diagnostics.Debug>. È possibile ottenere lo stesso effetto utilizzando la classe <xref:System.Diagnostics.Trace> con compilazione condizionale, ad esempio `#ifdef DEBUG`... `#endif`. È possibile definire questi simboli nella **\<Project> finestra di dialogo Pagine delle** proprietà. Per altre informazioni, vedere [Modifica delle impostazioni di progetto per una configurazione di debug di Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) o [Modifica delle impostazioni di progetto per una configurazione di debug di C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

## <a name="assert-arguments"></a><a name="BKMK_Assert_arguments"></a>Argomenti del metodo Assert
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> e <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> accettano fino a tre argomenti. Il primo argomento obbligatorio è la condizione che si desidera verificare. Se si chiama <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> o <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName> con un solo argomento, il metodo `Assert` verifica la condizione e, se il risultato è false, genera il contenuto dello stack di chiamate nella finestra **Output**. Nell'esempio riportato di seguito sono illustrati i metodi <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> e <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName>:

```VB
Debug.Assert(stacksize > 0)
Trace.Assert(stacksize > 0)
```

```csharp
Debug.Assert ( stacksize > 0 );
Trace.Assert ( stacksize > 0 );
```

  Il secondo e il terzo argomento, se presenti, devono essere stringhe. Se si chiama il metodo <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> o <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> con due o tre argomenti, il primo argomento è una condizione. Il metodo verifica la condizione e, se il risultato è false, genera la seconda e la terza stringa. Nell'esempio riportato di seguito viene illustrato l'utilizzo di <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=fullName> e <xref:System.Diagnostics.Trace.Assert(System.Boolean,System.String)?displayProperty=fullName> con due argomenti:

```VB
Debug.Assert(stacksize > 0, "Out of stack space")
Trace.Assert(stacksize > 0, "Out of stack space")
```

```csharp
Debug.Assert ( stacksize > 0, "Out of stack space" );
Trace.Assert ( stacksize > 0, "Out of stack space" );
```

  L'esempio seguente <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=fullName> mostra e viene usato con tre <xref:System.Diagnostics.Trace.Assert(System.Boolean,System.String,System.String)?displayProperty=fullName> argomenti:

```VB
Debug.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:", "inctemp failed on third call" )
```

```csharp
Debug.Assert ( stacksize > 100, "Out of stack space" , "Failed in inctemp" );
Trace.Assert ( stacksize > 0, "Out of stack space", "Failed in inctemp" );
```

 [Contenuto dell'argomento](#BKMK_In_this_topic)

## <a name="customizing-assert-behavior"></a><a name="BKMK_Customizing_Assert_behavior"></a> Personalizzazione del comportamento di Assert
 Se l'applicazione viene eseguita nella modalità interfaccia utente, il metodo `Assert` visualizza la finestra di dialogo **Asserzione non riuscita** quando la condizione ha esito negativo. Le azioni che vengono eseguite quando un'asserzione ha esito negativo sono controllate dalla proprietà <xref:System.Diagnostics.Debug.Listeners%2A> o <xref:System.Diagnostics.Trace.Listeners%2A>.

 È possibile personalizzare il comportamento di output aggiungendo un oggetto <xref:System.Diagnostics.TraceListener> alla raccolta `Listeners`, rimuovendo un oggetto <xref:System.Diagnostics.TraceListener> dalla raccolta `Listeners` oppure eseguendo l'override del metodo <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> di un oggetto `TraceListener` esistente in modo da ottenere un comportamento diverso.

 È ad esempio possibile eseguire l'override del metodo <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> per scrivere in un log eventi anziché visualizzare la finestra di dialogo **Asserzione non riuscita**.

 Per personalizzare l'output in questo modo, il programma deve contenere un listener ed è necessario ereditare da <xref:System.Diagnostics.TraceListener>, nonché eseguire l'override del relativo metodo <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName>.

 Per altre informazioni, vedere [Listener di traccia.](/dotnet/framework/debug-trace-profile/trace-listeners)

 [Contenuto dell'argomento](#BKMK_In_this_topic)

## <a name="setting-assertions-in-configuration-files"></a><a name="BKMK_Setting_assertions_in_configuration_files"></a> Impostazione di asserzioni nei file di configurazione
 Le asserzioni possono essere impostate sia nel file di configurazione del programma sia nel codice. Per altre informazioni, vedere <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> o <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.

## <a name="see-also"></a>Vedi anche

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>
- <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Traccia e strumentazione di applicazioni](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [Procedura: Compilare in modo condizionale con traccia e debug](/dotnet/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug)
- [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Debug del codice gestito](../debugger/debugging-managed-code.md)
