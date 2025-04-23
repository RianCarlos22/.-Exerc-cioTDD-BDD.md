# .-Exerc-cioTDD-BDD.md    atividade em dupla - RIAN CARLOS DUTRA 42220061 / YURI CARLOS DUTRA 42220052
ReservaService.java
package reserva;

public class ReservaService {
    public String reservar(String cidade, String endereco) {
        if (cidade.equalsIgnoreCase("Belo Horizonte") || cidade.equalsIgnoreCase("Contagem")) {
            return "Motorista a caminho";
        } else {
            return "Área fora de cobertura";
        }
    }
}

ReservaServiceTest.java
package runner;

import org.junit.jupiter.api.Test;
import reserva.ReservaService;
import static org.junit.jupiter.api.Assertions.assertEquals;

public class ReservaServiceTest {

    private final ReservaService reservaService = new ReservaService();

    @Test
    public void testReservaDentroArea() {
        String resultado = reservaService.reservar("Belo Horizonte", "Rua A");
        assertEquals("Motorista a caminho", resultado);
    }

    @Test
    public void testReservaForaArea() {
        String resultado = reservaService.reservar("São Paulo", "Rua B");
        assertEquals("Área fora de cobertura", resultado);
    }
}

reserva.feature
Feature: Reserva de carro

  Scenario: Reserva dentro da área de cobertura
    Given que o passageiro está em "Belo Horizonte"
    And informou o endereço "Rua A"
    When ele solicita uma reserva
    Then o sistema retorna "Motorista a caminho"

  Scenario: Reserva fora da área de cobertura
    Given que o passageiro está em "São Paulo"
    And informou o endereço "Rua B"
    When ele solicita uma reserva
    Then o sistema retorna "Área fora de cobertura"
