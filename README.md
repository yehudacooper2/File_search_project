# File_search_project
USE [FileDb]
GO

/****** Object:  Table [dbo].[FileQuery]    Script Date: 23/07/2018 13:02:32 ******/
SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE TABLE [dbo].[FileQuery](
	[SearchId] [int] IDENTITY(1,1) NOT NULL,
	[SearchQuery] [nvarchar](50) NOT NULL,
 CONSTRAINT [PK_FileQuery] PRIMARY KEY CLUSTERED 
(
	[SearchId] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]

GO




USE [FileDb]
GO

/****** Object:  Table [dbo].[FileRes]    Script Date: 23/07/2018 13:02:56 ******/
SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE TABLE [dbo].[FileRes](
	[ResId] [int] IDENTITY(1,1) NOT NULL,
	[SearchId] [int] NOT NULL,
	[PathRes] [nvarchar](500) NULL,
	[ChoosenDirectory] [nvarchar](100) NULL,
 CONSTRAINT [PK_FileRes] PRIMARY KEY CLUSTERED 
(
	[ResId] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]

GO

ALTER TABLE [dbo].[FileRes]  WITH CHECK ADD  CONSTRAINT [FK_FileRes_FileQuery] FOREIGN KEY([SearchId])
REFERENCES [dbo].[FileQuery] ([SearchId])
GO

ALTER TABLE [dbo].[FileRes] CHECK CONSTRAINT [FK_FileRes_FileQuery]
GO


