
-- phpMyAdmin SQL Dump
-- version 5.2.1
-- https://www.phpmyadmin.net/
--
-- Host: 127.0.0.1
-- Tempo de geração: 08/04/2025 às 22:25
-- Versão do servidor: 10.4.32-MariaDB
-- Versão do PHP: 8.2.12

SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
START TRANSACTION;
SET time_zone = "+00:00";


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;

--
-- Banco de dados: `work2sell`
--

-- --------------------------------------------------------

--
-- Estrutura para tabela `categorias`
--

CREATE TABLE `categorias` (
  `id` bigint(20) UNSIGNED NOT NULL,
  `nome` varchar(100) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Despejando dados para a tabela `categorias`
--

INSERT INTO `categorias` (`id`, `nome`) VALUES
(1, 'abacate'),
(2, '1'),
(3, 'telemóvel'),
(4, 'computarias'),
(5, ''),
(6, 'computarias'),
(7, ''),
(8, 'frutas exóticas'),
(9, 'eletrônicos'),
(10, 'livros e revistas'),
(11, 'roupas e acessórios'),
(12, 'automóveis'),
(13, 'artesanato'),
(14, 'brinquedos'),
(15, 'casa e decoração'),
(16, 'cosméticos e beleza'),
(17, 'esportes e lazer'),
(18, 'frutas exóticas'),
(19, 'eletrônicos'),
(20, 'livros e revistas'),
(21, 'roupas e acessórios'),
(22, 'automóveis'),
(23, 'artesanato'),
(24, 'brinquedos'),
(25, 'casa e decoração'),
(26, 'cosméticos e beleza'),
(27, 'esportes e lazer');

-- --------------------------------------------------------

--
-- Estrutura para tabela `compras`
--

CREATE TABLE `compras` (
  `id` bigint(20) UNSIGNED NOT NULL,
  `id_item` bigint(20) UNSIGNED NOT NULL,
  `id_usuario` bigint(20) UNSIGNED NOT NULL,
  `status` enum('pendente','andamento','finalizado','') NOT NULL,
  `data` datetime NOT NULL DEFAULT current_timestamp(),
  `descricao` text DEFAULT NULL,
  `quantidade` int(11) NOT NULL,
  `valor` float NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Despejando dados para a tabela `compras`
--

INSERT INTO `compras` (`id`, `id_item`, `id_usuario`, `status`, `data`, `descricao`, `quantidade`, `valor`) VALUES
(1, 3, 2, 'pendente', '2025-04-08 10:00:00', 'Compra de celular novo', 1, 0),
(2, 4, 1, 'andamento', '2025-04-07 12:30:00', 'Aquisição de computador gamer', 2, 0),
(3, 5, 3, 'finalizado', '2025-04-05 14:45:00', 'Compra de cadeira ergonômica', 1, 0),
(4, 6, 4, 'pendente', '2025-04-08 09:00:00', 'Compra de tênis esportivo', 3, 0),
(5, 7, 5, 'andamento', '2025-04-06 16:20:00', 'Aquisição de brinquedo educativo', 2, 0),
(6, 8, 6, 'finalizado', '2025-04-03 17:10:00', 'Compra de sofá para sala de estar', 1, 0),
(7, 9, 2, 'finalizado', '2025-04-02 11:55:00', 'Compra de livro sobre programação', 1, 0),
(8, 10, 3, 'pendente', '2025-04-01 08:30:00', 'Aquisição de relógio inteligente', 1, 0),
(9, 11, 4, 'andamento', '2025-04-05 19:00:00', 'Compra de celular novo para a esposa', 1, 0),
(10, 12, 5, 'finalizado', '2025-04-07 13:40:00', 'Compra de acessórios para carro', 2, 0),
(11, 2, 1, 'andamento', '2025-04-08 16:16:37', 'Tudo zuado dms', 2, 1300),
(12, 2, 1, '', '2025-04-08 16:18:33', 'Tudo zuado dms', 2, 1300),
(13, 4, 7, 'pendente', '2025-04-08 16:20:13', 'nada a comentar', 1, 350);

-- --------------------------------------------------------

--
-- Estrutura para tabela `itens`
--

CREATE TABLE `itens` (
  `id` bigint(20) UNSIGNED NOT NULL,
  `id_categoria` bigint(20) UNSIGNED NOT NULL,
  `nome` varchar(100) NOT NULL,
  `descricao` text DEFAULT NULL,
  `valor` float(10,0) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Despejando dados para a tabela `itens`
--

INSERT INTO `itens` (`id`, `id_categoria`, `nome`, `descricao`, `valor`) VALUES
(1, 9, 'Smartphone XYZ', 'Celular com 128GB de armazenamento e câmera de 64MP', 2500),
(2, 8, 'Cadeira Ergonômica', 'Cadeira confortável para longas horas de trabalho', 650),
(3, 10, 'Livro: Programação para Iniciantes', 'Livro que ensina os primeiros passos na programação', 90),
(4, 11, 'Tênis de Corrida', 'Tênis ideal para corrida de alta performance', 350),
(5, 12, 'Brinquedo Educativo', 'Brinquedo que ajuda no desenvolvimento cognitivo das crianças', 120),
(6, 13, 'Sofá de 3 lugares', 'Sofá de estilo moderno com tecido resistente', 1200),
(7, 14, 'Relógio Inteligente', 'Relógio que monitora atividades físicas e tem funções de smartphone', 499),
(8, 15, 'Acessórios para Carro', 'Kit de acessórios automotivos para personalização do veículo', 250),
(9, 16, 'Creme Anti-Age', 'Creme facial para combater sinais de envelhecimento', 150),
(10, 17, 'Bola de Futebol', 'Bola profissional de futebol para jogos e treinos', 80),
(11, 9, 'Smartphone XYZ', 'Celular com 128GB de armazenamento e câmera de 64MP', 2500),
(12, 8, 'Cadeira Ergonômica', 'Cadeira confortável para longas horas de trabalho', 650),
(13, 10, 'Livro: Programação para Iniciantes', 'Livro que ensina os primeiros passos na programação', 90),
(14, 11, 'Tênis de Corrida', 'Tênis ideal para corrida de alta performance', 350),
(15, 12, 'Brinquedo Educativo', 'Brinquedo que ajuda no desenvolvimento cognitivo das crianças', 120),
(16, 13, 'Sofá de 3 lugares', 'Sofá de estilo moderno com tecido resistente', 1200),
(17, 14, 'Relógio Inteligente', 'Relógio que monitora atividades físicas e tem funções de smartphone', 499),
(18, 15, 'Acessórios para Carro', 'Kit de acessórios automotivos para personalização do veículo', 250),
(19, 16, 'Creme Anti-Age', 'Creme facial para combater sinais de envelhecimento', 150),
(20, 17, 'Bola de Futebol', 'Bola profissional de futebol para jogos e treinos', 80);

-- --------------------------------------------------------

--
-- Estrutura para tabela `usuarios`
--

CREATE TABLE `usuarios` (
  `id` bigint(20) UNSIGNED NOT NULL,
  `nome` varchar(100) NOT NULL,
  `email` varchar(100) NOT NULL,
  `senha` varchar(255) NOT NULL,
  `cpf` varchar(14) NOT NULL,
  `telefone` varchar(14) NOT NULL,
  `adm` tinyint(1) NOT NULL DEFAULT 0
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Despejando dados para a tabela `usuarios`
--

INSERT INTO `usuarios` (`id`, `nome`, `email`, `senha`, `cpf`, `telefone`, `adm`) VALUES
(1, 'João Silva', 'joao.silva@gmail.com', 'senha123', '123.456.789-01', '(11) 98765-432', 1),
(2, 'Maria Oliveira', 'maria.oliveira@gmail.com', 'senha123', '234.567.890-12', '(21) 99876-543', 0),
(3, 'Carlos Souza', 'carlos.souza@gmail.com', 'senha123', '345.678.901-23', '(31) 91234-567', 0),
(4, 'Ana Costa', 'ana.costa@gmail.com', 'senha123', '456.789.012-34', '(41) 92345-678', 1),
(5, 'Luana Pereira', 'luana.pereira@gmail.com', 'senha123', '567.890.123-45', '(51) 93456-789', 0),
(6, 'Ricardo Gomes', 'ricardo.gomes@gmail.com', 'senha123', '678.901.234-56', '(61) 94567-890', 0),
(7, 'Fernanda Lima', 'fernanda.lima@gmail.com', 'senha123', '789.012.345-67', '(71) 95678-901', 1),
(8, 'Paulo Martins', 'paulo.martins@gmail.com', 'senha123', '890.123.456-78', '(81) 96789-012', 0),
(9, 'Camila Rocha', 'camila.rocha@gmail.com', 'senha123', '901.234.567-89', '(91) 97890-123', 1),
(10, 'Gustavo Alves', 'gustavo.alves@gmail.com', 'senha123', '012.345.678-90', '(11) 98901-234', 0),
(11, 'João Silva', 'joao.silva@gmail.com', 'senha123', '123.456.789-01', '(11) 98765-432', 1),
(12, 'Maria Oliveira', 'maria.oliveira@gmail.com', 'senha123', '234.567.890-12', '(21) 99876-543', 0),
(13, 'Carlos Souza', 'carlos.souza@gmail.com', 'senha123', '345.678.901-23', '(31) 91234-567', 0),
(14, 'Ana Costa', 'ana.costa@gmail.com', 'senha123', '456.789.012-34', '(41) 92345-678', 1),
(15, 'Luana Pereira', 'luana.pereira@gmail.com', 'senha123', '567.890.123-45', '(51) 93456-789', 0),
(16, 'Ricardo Gomes', 'ricardo.gomes@gmail.com', 'senha123', '678.901.234-56', '(61) 94567-890', 0),
(17, 'Fernanda Lima', 'fernanda.lima@gmail.com', 'senha123', '789.012.345-67', '(71) 95678-901', 1),
(18, 'Paulo Martins', 'paulo.martins@gmail.com', 'senha123', '890.123.456-78', '(81) 96789-012', 0),
(19, 'Camila Rocha', 'camila.rocha@gmail.com', 'senha123', '901.234.567-89', '(91) 97890-123', 1),
(20, 'Gustavo Alves', 'gustavo.alves@gmail.com', 'senha123', '012.345.678-90', '(11) 98901-234', 0);

--
-- Índices para tabelas despejadas
--

--
-- Índices de tabela `categorias`
--
ALTER TABLE `categorias`
  ADD PRIMARY KEY (`id`),
  ADD UNIQUE KEY `id` (`id`);

--
-- Índices de tabela `compras`
--
ALTER TABLE `compras`
  ADD PRIMARY KEY (`id`),
  ADD UNIQUE KEY `id` (`id`),
  ADD KEY `id_item` (`id_item`),
  ADD KEY `id_usuario` (`id_usuario`);

--
-- Índices de tabela `itens`
--
ALTER TABLE `itens`
  ADD PRIMARY KEY (`id`),
  ADD UNIQUE KEY `id` (`id`),
  ADD KEY `id_categoria` (`id_categoria`);

--
-- Índices de tabela `usuarios`
--
ALTER TABLE `usuarios`
  ADD PRIMARY KEY (`id`),
  ADD UNIQUE KEY `id` (`id`);

--
-- AUTO_INCREMENT para tabelas despejadas
--

--
-- AUTO_INCREMENT de tabela `categorias`
--
ALTER TABLE `categorias`
  MODIFY `id` bigint(20) UNSIGNED NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=28;

--
-- AUTO_INCREMENT de tabela `compras`
--
ALTER TABLE `compras`
  MODIFY `id` bigint(20) UNSIGNED NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=14;

--
-- AUTO_INCREMENT de tabela `itens`
--
ALTER TABLE `itens`
  MODIFY `id` bigint(20) UNSIGNED NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=21;

--
-- AUTO_INCREMENT de tabela `usuarios`
--
ALTER TABLE `usuarios`
  MODIFY `id` bigint(20) UNSIGNED NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=21;

--
-- Restrições para tabelas despejadas
--

--
-- Restrições para tabelas `compras`
--
ALTER TABLE `compras`
  ADD CONSTRAINT `compras_ibfk_1` FOREIGN KEY (`id_item`) REFERENCES `itens` (`id`) ON DELETE CASCADE ON UPDATE CASCADE,
  ADD CONSTRAINT `compras_ibfk_2` FOREIGN KEY (`id_usuario`) REFERENCES `usuarios` (`id`) ON DELETE CASCADE ON UPDATE CASCADE;

--
-- Restrições para tabelas `itens`
--
ALTER TABLE `itens`
  ADD CONSTRAINT `itens_ibfk_1` FOREIGN KEY (`id_categoria`) REFERENCES `categorias` (`id`) ON DELETE CASCADE ON UPDATE CASCADE;
COMMIT;

/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
