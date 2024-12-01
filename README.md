erDiagram
    %% ENTIDADES PRINCIPALES
    SANCION {
        int idSancion
        int cantidad
        string estado
        int idDeportista
        int idJuez
        int idArbitro
    }
    PERSONA {
        int idPersona
        string nombre
        string apellidos
        string email
        date fechaNacimiento
        string codigoPostal
        string zona
        string direccion
        string telefono
        string idioma
        string contrasena
        int idCeremonia
        int idPais
    }
    PAIS {
        int idPais
        string continente
        string himno
    }
    CEREMONIA {
        int idCeremonia
        string ubicacion
        string tipoCeremonia
        date apertura
        date clausura
    }
    ARBITRO {
        int idArbitro
        string especialidadA
        string idioma
    }
    TUTOR {
        int idTutor
        string estadoCivil
        string ocupacion
        string tipo
        string rutas
        string rut
    }
    LESION {
        int idLesion
        string tipoLesion
        string severidad
        date fechaLesion
        int idPersona
    }
    MEDICO {
        int idMedico
        string especialidadM
    }
    ARTISTA {
        int idArtista
        string generoMus
        string nombreArtistico
        int idGrupoM
    }
    GRUPO_MUSICAL {
        int idGrupoM
        string trayectoria
    }
    ESPECTADOR {
        int idEspectador
        string tipo
        string metodoPago
    }
    BOLETO {
        int idBoleto
        float precio
        int idEspectador
    }
    D_MARATON {
        int idMaraton
        string tiempoLlegada
        string tiempoPartida
        string recordMundial
    }
    EQUIPO {
        int idEquipo
        date fecha
        string hora
        int idFutbol
    }
    FIXTURE_F {
        int idFixture_F
        date fecha
        string hora
        int idFutbol
    }
    D_FUTBOL {
        int idFutbol
        string lugar
    }
    GRUPO {
        int idGrupo
        string nombreG
        int idBaloncesto
        int idPais
    }
    FIXTURE_B {
        int idFixture_B
        int puntos_GA
        int puntos_GB
        int idBaloncesto
    }
    D_BALONCESTO {
        int idBaloncesto
        int punto
        string penal
    }
    D_BOXEO {
        int idBoxeo
        string caracteristica
    }
    FIXTURE_BX {
        int idFixture_BX
        int puntosBx
        string descripcion
        int idBoxeo
        int idArbitro
    }
    PARTICIPA_CERMONIA {
        int idCeremonia
        int idGrupoM
    }
    DISCIPLINA {
        int idDisciplina
        date fechaIni
        string edicion
        string horario
        string nombre_disciplina
    }
    TIENE {
        int idDisciplina
        int idBoleto
        int idSede
    }
    SEDE {
        int idSede
        int capacidad
        string estado
        string nombreSede
        string ubicacion
        int distanciaVilla
    }
    ORGANIZA {
        int idDisciplina
        int idSede
        date fechaIni
        date fechaFin
    }
    PATROCINA {
        int idPatrocinador
        int idSede
    }
    PATROCINADOR {
        int idPatrocinador
        string actividad
    }
    LLEGA {
        int idSede
        int idTransporte
        string hora_llegada
    }
    TRANSPORTE {
        int idTransporte
        string placa
        string modelo
        string rutas
        string tipo
    }
    TRANSPORTA {
        int idTransporte
        int idPersona
        string horaPartida
    }
    ES_PARTE {
        int idDisciplina
        int idPersonal
    }
    PERSONAL {
        int idPersonal
        string nombreP
        string rol
    }
    ASOCIADO {
        int idDisciplina
        int idEntrenador
    }
    ENTRENADOR {
        int idEntrenador
        string especialidad
        string rol
        string paisOrigen
    }
    PARTICIPA {
        int idDisciplina
        int idDeportista
    }
    PERTENECE {
        int idPatrocinador
        int idContrato
    }
    CONTRATO {
        int idContrato
        date fecha
        string detalle
    }
    COMPITEAT {
        int idDAtletismo
        int idDeportista
        string horaInicio
        string horaFin
    }
    POSEE {
        int idSede
        int idCentroSalud
    }
    CENTRO_SALUD {
        int idCentroSalud
        string ubicacion
    }
    AT_INGRESA {
        int idPersona
        int idCentroSalud
        string causa
        date fecha
    }
    COMPITEX {
        int idFixture_F
        int idEquipo
    }
    COMPITEY {
        int idFixture_F
        int idEquipo
    }
    REALIZA_GOL {
        int idFixture_F
        int idEquipo
        int idDeportista
        int minGol
        string penal
    }
    ASIGNADO_B {
        int idFixture_B
        int idArbitro
    }
    ASIGNADO_FUT {
        int idFixture_F
        int idArbitro
    }
    JUEZ {
        int idJuez
        string experiencia
        int idMaraton
    }
    D_ATLETISMO {
        int idDAtletismo
        string tiempoLlegada
        string recordMundial
        string tiempoPartida
        string subDisciplina
    }
    REGISTRO {
        int idDAtletismo
        int idPuntoControl
        string horarioPaso
    }
    PUNTO_CONTROL {
        int idPuntoControl
        string inicio
        string final
    }
    ATLETAX {
        int idFixture_Bx
        int idDeportista
    }
    ATLETAY {
        int idFixture_Bx
        int idDeportista
    }
    DEPORTISTA {
        int idDeportista
        string sistemaSalud
        string nacionalidad
        string biografia
        string sexo
        string Facebook
        string Instagram
        string twiter
        string seguroMedico
        string ocupacion
        int idCeremonia
        int idTutor
        int idMedico
        int idEquipo
    }

    %% RELACIONES ENTRE ENTIDADES
    PERSONA ||--o{ PAIS : "pertenece"
    PERSONA ||--o| CEREMONIA : "participa"
    LESION ||--o| PERSONA : "afecta"
    ARTISTA ||--o| GRUPO_MUSICAL : "pertenece"
    BOLETO ||--o| ESPECTADOR : "adquiere"
    DEPORTISTA ||--o| CEREMONIA : "asiste"
    DEPORTISTA ||--o| TUTOR : "tutor"
    DEPORTISTA ||--o| MEDICO : "atendido por"
    DEPORTISTA ||--o| SEDE : "compite"
    FIXTURE_F ||--o| SEDE : "se juega en"
    TRANSPORTE ||--o| PERSONA : "transporta"
    SANCION ||--o| JUEZ : "aplica"
    SANCION ||--o| ARBITRO : "evalua"
    DISCIPLINA ||--o| SEDE : "tiene"
    CONTRATO ||--o| DEPORTISTA : "contrata"
    GRUPO ||--o| PAIS : "representa"
    FIXTURE_F ||--o| DEPORTISTA : "participa"


    %% RELACIONES ENTRE ENTIDADES
    PERSONA ||--o{ PAIS : "pertenece"
    PERSONA ||--o| CEREMONIA : "participa"
    LESION ||--o| PERSONA : "afecta"
    ARTISTA ||--o| GRUPO_MUSICAL : "pertenece"
    BOLETO ||--o| ESPECTADOR : "adquiere"
    DEPORTISTA ||--o| CEREMONIA : "asiste"
    DEPORTISTA ||--o| TUTOR : "tutor"
    DEPORTISTA ||--o| MEDICO : "atendido por"
    DEPORTISTA ||--o| SEDE : "compite"
    FIXTURE_F ||--o| SEDE : "se juega en"
    TRANSPORTE ||--o| PERSONA : "transporta"
    SANCION ||--o| JUEZ : "aplica"
    SANCION ||--o| ARBITRO : "evalua"
    DISCIPLINA ||--o| SEDE : "tiene"
    CONTRATO ||--o| DEPORTISTA : "contrata"
    GRUPO ||--o| PAIS : "representa"
    FIXTURE_F ||--o| DEPORTISTA : "participa"

