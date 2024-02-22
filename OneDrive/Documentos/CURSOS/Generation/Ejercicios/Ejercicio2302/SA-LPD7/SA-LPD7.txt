import java.util.Scanner;

public class minutosrestantes {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int minutosTotalesHastaFinDeSemana = 0;

        while (true) {
            System.out.println("Ingrese el día de la semana (lunes a viernes):");
            String diaSemana = scanner.nextLine().toLowerCase(); 
            if (!diaSemana.equals("lunes") && !diaSemana.equals("martes") && !diaSemana.equals("miércoles")
                    && !diaSemana.equals("miercoles") && !diaSemana.equals("jueves") && !diaSemana.equals("viernes")) {
                System.out.println("Día de la semana inválido. Ingresa un día válido.");
                continue;
            }

            System.out.println("Ingresa la hora (0-23):");
            int hora = Integer.parseInt(scanner.nextLine());

            if (hora < 0 || hora > 23) {
                System.out.println("Hora inválida. Ingresa una hora válida.");
                continue;
            }

            System.out.println("Ingresa los minutos (0-59):");
            int minutos = Integer.parseInt(scanner.nextLine());

            if (minutos < 0 || minutos > 59) {
                System.out.println("Minutos inválidos. Ingresa minutos válidos.");
                continue;
            }

            minutosTotalesHastaFinDeSemana = calcularMinutosHastaFinDeSemana(diaSemana, hora, minutos);
            break;
        }

        System.out.println("Minutos hasta el fin de semana: " + minutosTotalesHastaFinDeSemana);

        scanner.close();
    }

    public static int calcularMinutosHastaFinDeSemana(String diaSemana, int hora, int minutos) {
        int minutosTotales = 0;

        switch (diaSemana) {
            case "lunes":
                minutosTotales = (4 * 24 * 60) - ((hora * 60) + minutos);
                break;
            case "martes":
                minutosTotales = (3 * 24 * 60) - ((hora * 60) + minutos);
                break;
            case "miércoles":
            case "miercoles":
                minutosTotales = (2 * 24 * 60) - ((hora * 60) + minutos);
                break;
            case "jueves":
                minutosTotales = (1 * 24 * 60) - ((hora * 60) + minutos);
                break;
            case "viernes":
                minutosTotales = (15 * 60) - ((hora * 60) + minutos);
                break;
            default:
                break;
        }

        return minutosTotales;
    }
}
