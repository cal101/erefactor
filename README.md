# erefactor

## TL;DR

Erefactor is an eclipse based "Continuous Maintenance" tool that integrates into
git merge/pull request based web workflows and delivers automatic java code cleanups
(hopefully) ready for review and integration.

## Motivation

Tools like the great AutoRefactor eclipse plugin (https://github.com/JnRouvignac/AutoRefactor)
or modern IDEs in general offer a lot of cleanups. They can be executed on demand or may be executed
automatically on code save.

Cleanups start with formatting but also includes cleanups for removing useless stuff, following
good practices or migrating away from deprecated features.

So less manual work to be done to get better code easily.

But unfortunately tools like AutoRefactor don't get the attention and credit they deserve.
AutoRefactor is an impressive tool and was initially created by Jean-Noël Rouvignac and is now mostly
developed by Fabrice Tiercelin.

So why not combine these tools with modern CI/CD practices and tools and provide
cleanups right to the development workflow as merge/pull requests.

Erefactor tries to help with this.

But note that the tools have bugs and even by avoiding a null pointer exception
the software behavior may change in unexpected ways.

Therefore manual review is highly recommended.

## Technical

Erefactor is an eclipse application that applies cleanups/refactorings supplied by some *Provider*.

Currently only one provider is available, more are planned.

Please use the issues for questions or suggestions.

# Providers

## AutoRefactor

Repository: https://github.com/JnRouvignac/AutoRefactor

For more information see: http://autorefactor.org

See here for samples: http://autorefactor.org/html/samples.html

Available cleanups/refactorings:

```
    AddAllRatherThanLoopCleanUp - Collections.addAll() rather than loop (pre-configured)
        Collection related refactorings:
        - replaces for/foreach loops to use Collections.addAll() where 
        possible,
        - replaces for/foreach loops to use Collection.addAll() where 
        possible,
        - replaces for/foreach loops to use Collection.removeAll() where 
        possible.
    AddBracketsToControlStatementCleanUp - Add brackets to control statement (pre-configured)
        Adds brackets to:
        - if then/else clauses,
        - for loop body,
        - do ... while loop body,
        - while loop body.
    AggregateConstructorRatherThanGWTMethodCleanUp - Aggregate constructor rather than GWT method (pre-configured)
        Use new ArrayList<>() and new HashMap<>() instead of using specific 
        GWT Lists.newArrayList() and Maps.newHashMap().
    AndConditionRatherThanEmbededIfCleanUp - Collapse if statements (pre-configured)
        Merge inside if statement into the parent if statement.
    AndroidViewHolderCleanUp - Android ViewHolder (pre-configured)
        Android - Optimize getView() routines for Android applications. It 
        reduces the number calls to the costly inflate()) and getViewById() 
        Android API methods.
    AndroidWakeLockCleanUp - Android WakeLock (pre-configured)
        Android - Failing to release a wakelock properly can keep the 
        Android device in a high power mode, which reduces battery life. 
        There are several causes for this, such as releasing the wake lock 
        in onDestroy() instead of in onPause(), failing to call release() in 
        all possible code paths after an acquire(), and so on.
    AnnotationCleanUp - Annotation (pre-configured)
        Simplifies annotation uses:
        - empty parentheses will be removed from annotations,
        - single members named "value" will be removed from annotations and 
        only the value will be left.
    ArrayDequeRatherThanStackCleanUp - ArrayDeque rather than Stack (pre-configured)
        Replace Stack by ArrayDeque when possible.
    ArrayListRatherThanLinkedListCleanUp - ArrayList rather than LinkedList (pre-configured)
        Replace LinkedList by ArrayList when no item is inserted or removed 
        in the middle of the list.
    ArrayListRatherThanVectorCleanUp - ArrayList rather than Vector (pre-configured)
        Replace Vector by ArrayList when possible.
    AssertJCleanUp - Assert J (pre-configured)
        Refactors to a proper use of Assert J assertions.
    AssignRatherThanFilterThenAssignAnywayCleanUp - Assign rather than filter then assign anyway (pre-configured)
        Removes useless bad value checks before assignments or return 
        statements.
        Such useless bad value checks are comparing an expression against 
        bad value,
        then either assigning bad value or the expression depending on the 
        result of the bad value check.
        It is simpler to directly assign the expression.
    AssignRatherThanTernaryFilterThenAssignAnywayCleanUp - Assign rather than ternary filter then assign anyway
      (pre-configured)
        Removes useless bad value checks before assignments or return 
        statements.
        Such useless bad value checks are comparing an expression against 
        bad value,
        then either assigning bad value or the expression depending on the 
        result of the bad value check.
        It is simpler to directly assign the expression.
    AtomicObjectRatherThanMonoIndexArrayCleanUp - Atomic object rather than mono index array (pre-configured)
        Replace an array with one index by an atomic object.
    AutoBoxingRatherThanExplicitMethodCleanUp - AutoBoxing rather than explicit method (pre-configured)
        Remove useless valueOf() call to use AutoBoxing.
    BigNumberCleanUp - Big number (pre-configured)
        Refactors to a proper use of BigDecimals and BigIntegers:
        - create BigDecimals or BigIntegers from Strings rather than 
        floating point values,
        - create BigDecimals or BigIntegers from integers rather than String 
        representing integers,
        - use BigDecimal or BigInteger constants,
        - replace calls to equals() with calls to compareTo().
    BooleanCleanUp - Boolean (pre-configured)
        Boolean related refactorings:
        - remove if statements when then and else clauses do similar things 
        with opposite boolean values,
        - remove ternary operators when then and else clauses do similar 
        things with opposite boolean values,
        - simplify boolean expressions.
    BooleanConstantRatherThanValueOfCleanUp - Boolean constant rather than valueOf() (pre-configured)
        Replace Boolean.valueOf(true) and Boolean.valueOf(false) by Boolean.
        TRUE and Boolean.FALSE.
    BooleanEqualsRatherThanNullCheckCleanUp - Boolean equals() rather than null check (pre-configured)
        Replace a null check of a Boolean followed by its value by an 
        equality with a boolean constant.
    BooleanPrimitiveRatherThanWrapperCleanUp - Boolean primitive rather than wrapper (pre-configured)
        Replace Boolean wrapper object by boolean primitive type when an 
        object is not necessary.
    BracketsRatherThanArrayInstantiationCleanUp - Brackets rather than array instantiation (pre-configured)
        Replace the new instance syntax by curly brackets to create an array 
        when possible.
    BreakRatherThanPassiveIterationsCleanUp - Break rather than passive loops (pre-configured)
        Add a break to avoid passive for loop iterations.
    BytePrimitiveRatherThanWrapperCleanUp - Byte primitive rather than wrapper (pre-configured)
        Replace Byte wrapper object by byte primitive type when an object is 
        not necessary.
    CharPrimitiveRatherThanWrapperCleanUp - Char primitive rather than wrapper (pre-configured)
        Replace Character wrapper object by char primitive type when an 
        object is not necessary.
    CollectionCleanUp - Inited collection rather than new collection and Collection.addAll() (pre-configured)
        Replaces creating a new Collection, then invoking Collection.addAll()
         on it, by creating the new Collection with the other Collection as 
        parameter.
    CollectionsAddAllRatherThanAsListCleanUp - Collections.addAll() rather than Arrays.asList() (pre-configured)
        Directly add an array content into a collection using Collections.
        addAll() instead of converting the array into a list and then add 
        the elements into another collection.
    CommentsCleanUp - Comments (pre-configured)
        Refactors comments:
        - remove empty comments and javadocs,
        - transform comments applicable to java elements into javadocs,
        - transform javadocs that are not attached to any java elements into 
        block comments,
        - remove IDE generated TODOs,
        - remove empty lines at start and end of javadocs and block comments,
        - uppercase first letter of javadocs,
        - collapse javadocs on a single line when allowed by Eclipse 
        settings for formatting,
        - add final '.' to javadocs that do not have any,
        - remove Eclipse generated (non-Javadoc) block comments.
    CommonCodeInIfElseStatementCleanUp - Extract common code in if else statement (pre-configured)
        Factorizes common code in all if / else if / else statements at the 
        end of each blocks.
        Ultimately it removes the empty and passive if conditions.
    CommonIfInIfElseCleanUp - Move common inner if statement from then/else clauses around outer if statement
      (pre-configured)
        Moves an inner if statement around the outer if condition, when the 
        inner if condition is common to both if/else clauses of the outer if 
        statement.
    ComparisonCleanUp - Comparison to 0 rather than 1 or -1 (pre-configured)
        Fix Comparable.compareTo() usage. Beware! The behavior may change if 
        you implement a custom comparator!
    ContainsAllRatherThanLoopCleanUp - Collection.containsAll() rather than loop (pre-configured)
        Replace for loop with Collection.containsAll(Collection obj).
    ContainsRatherThanLoopCleanUp - Collection.contains() rather than loop (pre-configured)
        Replace for loop with Collection.contains(Object obj).
    DeclarationOutsideLoopRatherThanInsideCleanUp - Declaration outside loop rather than inside (pre-configured)
        Move declarations of variable inside a loop outside of the loop.
    DisjointRatherThanLoopCleanUp - Collections.disjoint() rather than loop (pre-configured)
        Replace for loop with Collections.disjoint(Collection obj1, 
        Collection obj2).
    DoWhileRatherThanDuplicateCodeCleanUp - Do/while rather than duplicate code (pre-configured)
        Replace while by do/while when the loop statements are duplicated 
        before the loop.
    DoWhileRatherThanWhileCleanUp - Do/while rather than while (pre-configured)
        Replace while by do/while when the first evaluation is always true.
    DoubleCompareRatherThanEqualityCleanUp - Double compare rather than equality (pre-configured)
        Replace arithmetic comparison by Double.compare(). Beware! The 
        behavior may change if your code run with a bug!
    DoubleNegationCleanUp - Double negation (pre-configured)
        Reduces double negation in boolean expression.
    DoublePrimitiveRatherThanWrapperCleanUp - Double primitive rather than wrapper (pre-configured)
        Replace Double wrapper object by double primitive type when an 
        object is not necessary.
    ElseRatherThanOppositeConditionCleanUp - Else rather than opposite condition (pre-configured)
        Remove a condition on an else that is opposite to the condition of 
        the previous if. Beware! It may change the behavior if the code is 
        transpiled in JavaScript for NaN values.
    EndOfLoopRatherThanContinueCleanUp - End of loop rather than continue (pre-configured)
        Removes useless lone continue at the end of a loop.
    EndOfMethodRatherThanReturnCleanUp - End of method rather than return (pre-configured)
        Removes useless lone return at the end of a method.
    EntrySetRatherThanKeySetAndValueSearchCleanUp - Map.entrySet() rather than Map.keySet() and value search
      (pre-configured)
        Convert for loops iterating on Map.keySet() to iterate on Map.
        entrySet() when possible. Beware! It may change the behavior if you 
        use custom Map implementation!
    EnumMapRatherThanHashMapCleanUp - EnumMap rather than HashMap for enum keys (pre-configured)
        Refactor implementation class HashMap -> EnumMap when key is an enum 
        type. Beware! It changes the result of an instanceof expression!
    EnumSetRatherThanHashSetCleanUp - EnumSet rather than HashSet for enum types (pre-configured)
        Converts creation of HashSet with enum as a type to invocation of 
        static methods of EnumSet where possible. Beware! It changes the 
        result of an instanceof expression!
    EqualsNullableCleanUp - Equals nullable (pre-configured)
        Removes redundant null checks or useless right-hand side or left-
        hand side operands.
    FillRatherThanLoopCleanUp - Arrays.fill() rather than loop (pre-configured)
        Replaces for loops to use Arrays.fill() where possible.
    FloatPrimitiveRatherThanWrapperCleanUp - Float primitive rather than wrapper (pre-configured)
        Replace Float wrapper object by float primitive type when an object 
        is not necessary.
    FormattedNumberRatherThanPackedNumberCleanUp - Formatted number rather than packed number (pre-configured)
        Add underscore for each thousand in number literals when it is 
        obvious it is useful. Unfortunately, only few cases are obvious.
    GenericListRatherThanRawListCleanUp - Generic list rather than raw list (pre-configured)
        Genericize a list if possible.
    GenericMapRatherThanRawMapCleanUp - Generic map rather than raw map (pre-configured)
        Genericize a map if possible.
    HashMapRatherThanHashtableCleanUp - HashMap rather than Hashtable (pre-configured)
        Replace Hashtable by HashMap when possible.
    HashMapRatherThanTreeMapCleanUp - HashMap rather than TreeMap (pre-configured)
        Replace TreeMap by HashMap when the entry order is not used.
    HashSetRatherThanTreeSetCleanUp - HashSet rather than TreeSet (pre-configured)
        Replace TreeSet by HashSet when the entry order is not used.
    IfElseIfCleanUp - if-elseif (pre-configured)
        Refactors "else { if (...) {} }" to "else if (...) {}".
    IfRatherThanTwoSwitchCasesCleanUp - If rather than two switch cases (pre-configured)
        Replace a switch structure by an if block when there are less than 
        three distinct cases. Beware! It may fix some null pointers, so it 
        may change the behavior.
    IfRatherThanWhileAndFallsThroughCleanUp - If rather than while and falls through (pre-configured)
        Replace a while loop that always terminates during the first 
        iteration by an if.
    ImplicitDefaultConstructorRatherThanWrittenOneCleanUp - Implicit default constructor rather than
      written one (pre-configured)
        Remove single public constructor with no arguments, no annotation 
        and no code.
    IncrementStatementRatherThanIncrementExpressionCleanUp - Increment statement rather than increment
      expression (pre-configured)
        Moves increment or decrement outside an expression when possible.
    InlineCodeRatherThanPeremptoryConditionCleanUp - Inline code rather than peremptory condition
      (pre-configured)
        Replace always true or always false condition by inline code.
    InstanceofRatherThanIsInstanceCleanUp - instanceof rather than isInstance() (pre-configured)
        Use an instanceof expression to check an object against a hardcoded 
        class.
    IntPrimitiveRatherThanWrapperCleanUp - Int primitive rather than wrapper (pre-configured)
        Replace Integer wrapper object by int primitive type when an object 
        is not necessary.
    InvertEqualsCleanUp - Equals on constant rather than on variable (pre-configured)
        Inverts calls to Object.equals(Object) and String.equalsIgnoreCase
        (String) when it is known that the second operand is not null and 
        the first can be null. Beware! By avoiding null pointer, the 
        behavior may change!
    IsEmptyRatherThanSizeCleanUp - Empty test rather than size (pre-configured)
        Replaces some checks on Collection.size() or Map.size() with checks 
        on isEmpty().
    JUnitAssertCleanUp - JUnit asserts (pre-configured)
        Refactors to a proper use of JUnit assertions.
    Java7HashRatherThanEclipseJava6HashCleanUp - Java 7 hash rather than Eclipse Java 6 hash (pre-configured)
        Rewrites Eclipse-autogenerated hashcode method by Eclipse-
        autogenerated hashcode method for Java 7.
    JoinRatherThanLoopCleanUp - String.join() rather than loop (pre-configured)
        Replaces for loops to use String.join() where possible.
    JupiterAssertCleanUp - Jupiter asserts (pre-configured)
        Refactors to a proper use of JUnit 5 assertions.
    LambdaCleanUp - Improve lambda expressions (pre-configured)
        Improve lambda expressions.
    LambdaExpressionRatherThanComparatorCleanUp - Lambda expression rather than comparator (pre-configured)
        Replace a plain comparator instance by a lambda expression passed to 
        a Comparator.comparing() method.
    LazyLogicalRatherThanEagerCleanUp - Lazy logical rather than eager (pre-configured)
        Replace & by && and | by || when the right operand is passive.
    LiteralRatherThanBooleanConstantCleanUp - Literal rather than boolean constant (pre-configured)
        Replace Boolean.TRUE/Boolean.FALSE by true/false on primitive 
        assignment.
    LocalVariableRatherThanFieldCleanUp - Local variable rather than field (pre-configured)
        Refactors a field into a local variable if its use is only local.
    LogParametersRatherThanLogMessageCleanUp - Log parameters rather than log message (pre-configured)
        Replaces a string concatenation as parameter of a logger method by a 
        string template followed by objects.
    LongPrimitiveRatherThanWrapperCleanUp - Long primitive rather than wrapper (pre-configured)
        Replace Long wrapper object by long primitive type when an object is 
        not necessary.
    MapCleanUp - Inited map rather than new map and Map.putAll() (pre-configured)
        Replaces creating a new Map, then invoking Map.putAll() on it, by 
        creating the new Map with the other Map as parameter.
    MergeConditionalBlocksCleanUp - Merge conditional statements (pre-configured)
        Merge adjacent if / else if / else statements with same code block.
    MethodOnMapRatherThanMethodOnKeySetCleanUp - Method on map rather than method on keyset (pre-configured)
        Directly invoke methods on Map rather than on Map.keySet() when 
        possible.
    NIORatherThanIOCleanUp - NIO rather than IO (pre-configured)
        Use java.nio.* classes instead of java.io.* classes.
    NamedMethodRatherThanLogLevelParameterCleanUp - Named method rather than log level parameter (pre-configured)
        Replaces level parameter by the appropriate method for standard 
        logging.
    NoAssignmentInIfConditionCleanUp - No assignment in if condition (pre-configured)
        Moves assignments inside an if condition before the if node.
    NoLoopIterationRatherThanEmptyCheckCleanUp - No loop iteration rather than empty check (pre-configured)
        Removes useless empty check before a for loop.
    ORConditionRatherThanRedundantClausesCleanUp - OR condition rather than redundant clauses (pre-configured)
        Replace (X && Y) || !X by Y || !X.
    ObjectsEqualsRatherThanEqualsAndNullCheckCleanUp - Objects equals rather than equals and null check (pre-configured)
        Simplify the equality between two objects.
    OneConditionRatherThanUnreachableBlockCleanUp - One condition rather than unreachable block (pre-configured)
        Detect two successive if conditions that are identical and remove 
        the second one.
    OneIfRatherThanDuplicateBlocksThatFallThroughCleanUp - One if rather than duplicate blocks that fall through
      (pre-configured)
        Merge consecutive if statements with same code block that end with a 
        jump statement.
    OneTryRatherThanTwoCleanUp - One try rather than two (pre-configured)
        Merge two embedded try statements into one.
    OperandFactorizationCleanUp - Operand factorization (pre-configured)
        Replace (X && Y) || (X && Z) by (X && (Y || Y)).
    OppositeComparisonRatherThanNegativeExpressionCleanUp - Opposite comparison rather than negative expression
      (pre-configured)
        Reverse a comparison expression to avoid a minus prefix.
    OppositeConditionRatherThanDuplicateConditionCleanUp - Opposite condition rather than duplicate condition
      (pre-configured)
        Do not repeat the same condition in several if.
    OptimizeRegExCleanUp - Optimize RegEx (pre-configured)
        Detect strings that are used as regular expression and rewrite it in 
        a more efficient way.
    OutsideCodeRatherThanFallingThroughBlocksCleanUp - Outside code rather than falling through blocks (pre-configured)
        Merge blocks that end with a jump statement into the following same 
        code.
    ParsingRatherThanValueOfCleanUp - Parsing rather than valueOf() (pre-configured)
        Avoid to create primitive wrapper when parsing a string.
    PatternRatherThanRegExStringCleanUp - Pattern Rather Than RegEx String (pre-configured)
        Compile a regular expression before using it.
    PrimitiveComparisonRatherThanWrapperComparisonCleanUp - Primitive comparison rather than wrapper comparison
      (pre-configured)
        Replace the compareTo() method by a comparison on primitive.
    PushNegationDownCleanUp - Push negation down (pre-configured)
        Pushes negations down, inside the negated expressions.
    ReduceIndentationCleanUp - Reduce indentation (pre-configured)
        Remove useless indentation when the opposite workflow falls through.
    RedundantBooleanCleanUp - Redundant boolean (pre-configured)
        Removes neutral operand in logical expression and removes 
        unreachable operands.
    RedundantModifiersCleanUp - Remove useless modifiers (pre-configured)
        Sorts modifiers.
        Also removes modifiers implied by the context:
        - "static" and "abstract" for interface,
        - "public", "static" and "final" for interface fields,
        - "public" and "abstract" for interface methods,
        - "final" for private methods,
        - "final" for parameters in interface method declarations,- 
        "protected" modifier for final class not inherited members.
    RedundantTruthCleanUp - Redundant truth (pre-configured)
        Directly checks boolean values instead of comparing them with 
        true/false.
    RemoveEmptyIfCleanUp - Remove empty if (pre-configured)
        Removes empty if or else block.
    RemoveEmptyLinesCleanUp - Remove empty lines (pre-configured)
        Removes unnecessary empty lines from source code:
        - empty lines after opening braces,
        - empty lines before closing braces,
        - two consecutive empty lines are converted to a single empty line.
    RemoveEmptyStatementCleanUp - Removes empty statements (pre-configured)
        Removes structural statements with no substatement.
    RemoveEmptySuperConstrInvocationCleanUp - Remove super() call in constructor (pre-configured)
        Remove call to super constructor with empty arguments since it is 
        redundant. See JLS section 12.5 for more info.
    RemoveFieldsDefaultValuesCleanUp - Remove fields default values (pre-configured)
        Removes field initializers when they are the default value of the 
        field's types.
        For example, the initializer will be removed for integer fields 
        initialized to "0".
        Likewise, the initializer will be removed for non primitive fields 
        initialized to "null".
    RemoveOverriddenAssignmentCleanUp - Remove overridden assignment (pre-configured)
        Remove passive assignment when the variable is reassigned before 
        being read.
    RemoveParenthesisCleanUp - Remove parenthesis (pre-configured)
        Remove useless parentheses.
    RemoveSemiColonCleanUp - Remove semicolons (pre-configured)
        Removes superfluous semicolon after body declarations in type 
        declarations.
    RemoveUncheckedThrowsClausesCleanUp - Remove unchecked exceptions from throws clause (pre-configured)
        Remove unchecked exceptions from throws clause. Beware, the JavaDoc 
        is not updated!
    RemoveUnnecessaryCastCleanUp - Remove unnecessary casts (pre-configured)
        Removes unnecessary widening casts from return statements, 
        assignments and infix expressions. Correctly types literals.
    RemoveUnnecessaryLocalBeforeReturnCleanUp - Remove unnecessary local before return (pre-configured)
        Removes unnecessary local variable declaration or unnecessary 
        variable assignment before a return statement.
    RemoveUnneededThisExpressionCleanUp - Remove unneeded this expressions (pre-configured)
        Remove useless use of "this" from method calls.
    RemoveUselessBlockCleanUp - Remove useless block (pre-configured)
        Removes lone and embedded block.
    SeparateAssertionsRatherThanBooleanExpressionCleanUp - Separate assertions rather than boolean expression
      (pre-configured)
        Refactors a true or a false assertion with respectively an AND or an 
        OR operator into two separate assertions. It works for JUnit and 
        TestNG.
    SerializeRatherThanBoxingAndSerializeCleanUp - Serialize rather than boxing and serialize (pre-configured)
        Replace a primitive boxing to serialize by a call to the static 
        toString() method.
    SetRatherThanListCleanUp - Set rather than List (pre-configured)
        Replace List by HashSet when only presence of items is used.
    SetRatherThanMapCleanUp - Set rather than map (pre-configured)
        Replace map by set when values are not read.
    ShortPrimitiveRatherThanWrapperCleanUp - Short primitive rather than wrapper (pre-configured)
        Replace Short wrapper object by short primitive type when an object 
        is not necessary.
    SimpleNameRatherThanQualifiedNameCleanUp - Simple name rather than qualified name (pre-configured)
        Refactors types, method invocations and field accesses to replace 
        qualified names by simple names when appropriate. For example when 
        relevant imports exist.
    SingleDeclarationsRatherThanMultiDeclarationCleanUp - Single declarations rather than multi declaration
      (pre-configured)
        Write only one variable declaration per line.
    StandardMethodRatherThanLibraryMethodCleanUp - Standard method rather than Library method (pre-configured)
        Stop using ObjectUtils.equals(), ObjectUtils.hashCode(), ObjectUtils.
        hashCodeMulti() and ObjectUtils.toString() to use java.util.Objects 
        methods instead.
    StaticConstantRatherThanInstanceConstantCleanUp - Static constant rather than instance constant (pre-configured)
        Add the static modifier to the initialized final primitive or 
        wrapper fields.
    StaticInnerClassThanNonStaticCleanUp - Static inner class than non-static (pre-configured)
        Make inner class static if it doesn't use top level class members.
    StringBuilderCleanUp - StringBuilder (pre-configured)
        Refactors to a proper use of StringBuilders:
        - replace String concatenations using operator '+' as parameters of 
        StringBuffer/StringBuilder.append(),
        - replace chained call to StringBuffer/StringBuilder constructor 
        followed by calls to append() and call toString() with straight 
        String concatenation using operator '+'.
    StringBuilderMethodRatherThanReassignationCleanUp - StringBuilder method call rather than reassignment
     (pre-configured)
        Removes the assignment to the same variable on a StringBuilder.
        append() call.
    StringBuilderRatherThanStringBufferCleanUp - StringBuilder rather than StringBuffer (pre-configured)
        Replace StringBuffer by StringBuilder when possible.
    StringBuilderRatherThanStringCleanUp - StringBuilder rather than String (pre-configured)
        Replace String concatenation by StringBuilder when possible.
    StringCleanUp - String (pre-configured)
        Removes:
        - calling String.toString() on a String instance,
        - remove calls to String.toString() inside String concatenations,
        - replace useless case shifts for equality by equalsIgnoreCase()
        Refactors:
        - usages of 'indexOf' and 'lastIndexOf' with single letter in string
    StringRatherThanNewStringCleanUp - String rather than new string (pre-configured)
        Removes a String instance from a String literal.
    StringValueOfRatherThanConcatCleanUp - String.valueOf() rather than concatenation (pre-configured)
        Replace forced string transformation by String.valueOf().
    SubstringWithOneParameterRatherThanTwoCleanUp - substring() with one parameter rather than two (pre-configured)
        Remove the second substring() parameter if this parameter is the 
        length of the string.
    SuperCallRatherThanUselessOverridingCleanUp - Super call rather than useless overriding (pre-configured)
        Removes overriding of method if the overriding only call the super 
        class.
    SwitchCleanUp - Switch (pre-configured)
        Switch related refactorings:
        - replaces if/else if/else blocks to use switch where possible.
    TernaryOperatorRatherThanDuplicateConditionsCleanUp - Ternary operator rather than duplicate conditions (pre-configured)
        Replace (X && Y) || (!X && Z) by X ? Y : Z.
    TestNGAssertCleanUp - TestNG asserts (pre-configured)
        Refactors to a proper use of TestNG assertions.
    TruncatingAppendingRatherThanSubCharactersCleanUp - Truncating appending rather than sub-characters (pre-configured)
        Use the specific StringBuffer/StringBuilder.append() methods with 
        their parameter to truncate strings
    TryWithResourceCleanUp - Use try-with-resource (pre-configured)
        Changes code to make use of Java 7 try-with-resources feature. In 
        particular, it removes now useless finally clauses.
    UnboxingRatherThanExplicitMethodCleanUp - Unboxing rather than explicit method (pre-configured)
        Remove useless primitiveValue() call to use unboxing.
    UpdateSetRatherThanTestingFirstCleanUp - Update set rather than testing first (pre-configured)
        Set related refactorings:
        - replaces calls to Set.contains() immediately followed by Set.add() 
        with straight calls to Set.add(),
        - replaces calls to Set.contains() immediately followed by Set.
        remove() with straight calls to Set.remove(). Beware! It may change 
        the behavior if you use custom Set implementation!
    UppercaseNumberSuffixRatherThanLowercaseCleanUp - Capitalize lower case 'l' -> 'L' for long
      'f' -> 'F' for float number literals (pre-configured)
        Capitalize lower case 'l' -> 'L' for long 'f' -> 'F' for float 
        number literals.
    UseDiamondOperatorCleanUp - Diamond operator (pre-configured)
        Refactors class instance creations to use the diamond operator 
        wherever possible.
    UseMultiCatchCleanUp - Multi-catch (pre-configured)
        Refactors catch clauses with the same body to use Java 7's multi-
        catch.
    UseStringContainsCleanUp - Use String.contains() (pre-configured)
        Replaces uses of String.indexOf(String) String.lastIndexOf(String) 
        by String.contains(CharSequence) where appropriate.
    ValueOfRatherThanInstantiationCleanUp - valueOf() rather than instantiation (pre-configured)
        Replaces unnecessary primitive wrappers instance creations by using 
        static factory methods ("valueOf()").
    VariableInsideIfRatherThanAboveCleanUp - Variable inside if rather than above (pre-configured)
        Move a variable assignment that is only used in an if inside the if 
        clause.
    VectorOldToNewAPICleanUp - Collections APIs rather than Vector pre-Collections APIs (pre-configured)
        Replaces Vector pre-Collections APIs with equivalent Collections 
        APIs.
    WhileConditionRatherThanInnerIfCleanUp - While condition rather than inner if (pre-configured)
        Move a condition of an inner if that breaks a while loop into the 
        while condition.
    XORRatherThanDuplicateConditionsCleanUp - XOR rather than duplicate conditions (pre-configured)
        Replace (X && !Y) || (!X && Y) by X ^ Y.
```

Note that the cleanups have different levels of usefulness and maturity.

Manual review is higly recommended.

Note also that some refactorings need a final formatting step which should be provided by the target project.

