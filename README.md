# BANCO-DE-DADOS-FALE_FACIL-
CREATE DATABASE fale_facil;
USE fale_facil;

CREATE TABLE Funcionarios_Seguranca (
    matricula INT(20) PRIMARY KEY,
    senha VARCHAR(255) NOT NULL
) ENGINE=InnoDB;

CREATE TABLE Categorias (
    id_C INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(50) NOT NULL UNIQUE
)ENGINE=InnoDB;


CREATE TABLE demandas (
    id INT AUTO_INCREMENT PRIMARY KEY,
    categoria ENUM('Áreas', 'Refeição', 'República', 'Segurança') NOT NULL,
    descricao TEXT NOT NULL,
    identificado BOOLEAN DEFAULT FALSE,
    nome_colaborador VARCHAR(100), -- Ficará vazio se for anônimo
    data_registro TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    status ENUM('Pendente', 'Em Tratativa', 'Resolvido') DEFAULT 'Pendente',
    CONSTRAINT fk_reclamacao_categoria FOREIGN KEY (categoria_id) REFERENCES Categorias(id),
    CONSTRAINT fk_demandas_funcionario FOREIGN KEY (funcionario_responsavel) REFERENCES Funcionarios_Seguranca(matricula) ON DELETE SET NULL
)ENGINE=InnoDB; 