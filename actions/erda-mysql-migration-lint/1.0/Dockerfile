# Copyright (c) 2021 Terminus, Inc.
#
# This program is free software: you can use, redistribute, and/or modify
# it under the terms of the GNU Affero General Public License, version 3
# or later ("AGPL"), as published by the Free Software Foundation.
#
# This program is distributed in the hope that it will be useful, but WITHOUT
# ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
# FITNESS FOR A PARTICULAR PURPOSE.
#
# You should have received a copy of the GNU Affero General Public License
# along with this program. If not, see <http://www.gnu.org/licenses/>.

FROM golang:1.15 AS builder

COPY . /go/src/github.com/erda-project/erda-actions
WORKDIR /go/src/github.com/erda-project/erda-actions

# go build action cmd
RUN GOPROXY=https://goproxy.io,direct GOOS=linux GOARCH=amd64 go build -o /opt/action/run actions/erda-mysql-migration-lint/1.0/internal/cmd/main.go

RUN chmod 777 /opt/action/run


FROM centos

MAINTAINER chenzhongrun "zhongrun.czr@alibaba-inc.com"

COPY --from=builder /opt/action/run /opt/action/run

RUN chmod 777 /opt/action/*
