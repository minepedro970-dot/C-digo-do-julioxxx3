data class Materia(
    val nome: String,
    val dificuldade: Double,
    val prazo: Double,
    val tempo: Double
)

fun calcularPrioridade(m: Materia): Double {
    var prioridade = m.dificuldade + m.tempo

    if (m.prazo <= 2.0) {
        prioridade += 5
    } else if (m.prazo <= 5.0) {
        prioridade += 3
    } else {
        prioridade += 1
    }

    return prioridade
}

fun main() {
    val tarefas = mutableListOf<Materia>()

    for (i in 1..3) {
        println("\nTarefa $i")

        print("Matéria: ")
        val nome = readln()

        print("Dificuldade: ")
        val dificuldade = readln().toDouble()

        print("Prazo (dias): ")
        val prazo = readln().toDouble()

        print("Tempo (horas): ")
        val tempo = readln().toDouble()

        tarefas.add(Materia(nome, dificuldade, prazo, tempo))
    }

    var maiorPrioridade = 0.0
    var maisImportante: Materia? = null

    for (t in tarefas) {
        val p = calcularPrioridade(t)
        println("\n${t.nome} → prioridade: $p")

        if (p > maiorPrioridade) {
            maiorPrioridade = p
            maisImportante = t
        }
    }

    println("\nMatéria mais importante: ${maisImportante?.nome}")
}
